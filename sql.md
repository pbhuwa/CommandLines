# Insert data query

```
CREATE TABLE sales (
id INT IDENTITY(1,1),
customer_name VARCHAR(100),
product_name VARCHAR(100),
sale_amount DECIMAL(10,2),
sale_date DATE
sale_date DATE
)

DECLARE @i INT = 1

WHILE @i <= 1000000
BEGIN
INSERT INTO sales (customer_name, product_name, sale_amount, sale_date)
VALUES (CONCAT('Customer', @i), CONCAT('Product', FLOOR(RAND()_(10-1+1)+1)),
FLOOR(RAND()_(1000-100+1)+100), DATEADD(day, -FLOOR(RAND()\*(365-1+1)+1), GETDATE()))
SET @i = @i + 1
END
```

# Calculate Delivery Weightage

```
CREATE PROCEDURE `sp_calculate_delivery_weightage`(
    IN p_location_id INT,
    IN min_weight FLOAT,
    IN max_weight FLOAT,
    IN base_rate DECIMAL(10,2),
    IN additional_rate DECIMAL(10,2),
    IN weight_interval FLOAT,
    IN remove_existing_record BOOL,
    IN fixed_charge bool
)
BEGIN
    DECLARE current_weight FLOAT;
    DECLARE current_rate DECIMAL(10,2);
    DECLARE next_weight FLOAT;

    SET current_weight = min_weight;
    SET current_rate = base_rate;

    IF remove_existing_record THEN
        DELETE FROM weight_settings WHERE location_id = p_location_id;
    ELSE
        DELETE FROM weight_settings WHERE location_id = p_location_id
        AND weight_from >= min_weight AND weight_to <= max_weight;
    END IF;
    CREATE TEMPORARY TABLE temp_weight_settings (
        shipping DECIMAL(10,2),
        weight_from FLOAT,
        weight_to FLOAT,
        created_at timestamp,
        updated_at timestamp,
        location_id INT
    );

    if fixed_charge=1 then
        INSERT INTO temp_weight_settings (shipping, weight_from, weight_to, created_at, updated_at, location_id)
        VALUES (base_rate, min_weight, max_weight, Now(), Now(),p_location_id);
    else
    WHILE current_weight < max_weight DO

    SET current_weight=current_weight+0.1;
        SET next_weight = current_weight + weight_interval - 0.1;

        INSERT INTO temp_weight_settings (shipping, weight_from, weight_to, created_at, updated_at, location_id)
        VALUES (current_rate, current_weight, next_weight, Now(), Now(),p_location_id);

        SET current_weight = next_weight;
        SET current_rate = current_rate + additional_rate;

    END WHILE;

    end if;

    INSERT INTO weight_settings (shipping, weight_from, weight_to, created_at, updated_at, location_id)
    SELECT shipping, weight_from, weight_to, created_at, updated_at, location_id FROM temp_weight_settings;

    DROP TEMPORARY TABLE IF EXISTS temp_weight_settings;
END
```
