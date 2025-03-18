# Personalize product query

```
CREATE PROCEDURE `SP_LandingPageData`( IN uId INT, IN categorySlugs text )
BEGIN
    DECLARE
        userCategoryCount INT DEFAULT 0;
    DECLARE
        currentDate DATETIME;
    DECLARE
        flashIds TEXT;
    DECLARE
        offerId INT;
    DECLARE
        offerName VARCHAR ( 255 );
    DECLARE
        conditions TEXT;
    DECLARE
        sqlQuery TEXT;
    DECLARE
        userSlugs TEXT;

    SET currentDate = NOW();
    DROP TEMPORARY TABLE
    IF
        EXISTS temp_flashSales;
    CREATE TEMPORARY TABLE temp_flashSales AS SELECT
    p.*
    FROM
        products p
        INNER JOIN flashes f ON f.product_id = p.id
        INNER JOIN categories c ON p.category_id = c.id
        AND c.parent_disabled = 0
        AND c.STATUS = 1
        LEFT JOIN brands b ON p.brand_id = b.id
        JOIN (
        SELECT
            `c`.`id` AS `category_id`,
            COALESCE ( `mpc`.`id`, `pc`.`id`, `c`.`id` ) AS `parent_category_id`
        FROM
            `categories` `c`
            LEFT JOIN `categories` `pc` ON ( `pc`.`id` = `c`.`parent_id` )
            LEFT JOIN `categories` `mpc` ON ( `mpc`.`id` = `pc`.`parent_id` )
        ) pacat ON p.category_id = pacat.category_id
        LEFT JOIN ( SELECT tc.parent_category_id, sum( tc.category_count ) 'count' FROM vw_user_trending_categories tc WHERE tc.user_id = uId GROUP BY tc.parent_category_id ) ptc ON pacat.parent_category_id = ptc.parent_category_id
    WHERE
        f.start_date <= Now() AND f.end_date >= Now()
        AND ( b.id IS NULL OR b.STATUS = 1 )
        AND p.STATUS = 1
        AND p.verified = 1
        AND p.deleted_at IS NULL
    ORDER BY
        f.on_home_page DESC,
        f.end_date ASC,
        ptc.count DESC,
        f.id
        LIMIT 12;
    SELECT
        *
    FROM
        temp_flashSales;
    SELECT
        GROUP_CONCAT( id ) INTO flashIds
    FROM
        ( SELECT p.id FROM temp_flashSales p LIMIT 10 ) AS limited_products;
    SELECT
        id,
        `name` INTO @offerId,
        @offerName
    FROM
        offers o
    WHERE
        o.STATUS = 'active'
        AND o.offer_type = 'CAMPAIGN'
        AND o.start_date <= CURRENT_DATE AND o.end_date >= CURRENT_DATE
    ORDER BY
        o.start_date DESC
        LIMIT 1;
    IF
        @offerId > 0 THEN
        SELECT
            GROUP_CONCAT( CONCAT( '(', 'brand_id IN (', brandIds, ') AND category_id IN (', categoryIds, ')', ')' ) SEPARATOR ' OR ' ) AS result INTO @conditions
        FROM
            (
            SELECT
                id,
                GROUP_CONCAT(DISTINCT REPLACE(REPLACE(REPLACE(brand_id, '[', ''), ']', ''), '"', '')) AS brandIds,
                GROUP_CONCAT(DISTINCT REPLACE(REPLACE(REPLACE(category_id, '[', ''), ']', ''), '"', '')) AS categoryIds
            FROM
                offers
            WHERE
                STATUS = 'active'
                AND offer_type = 'CAMPAIGN'
                AND start_date <= CURRENT_DATE AND end_date >= CURRENT_DATE
            GROUP BY
                id
            ORDER BY
                start_date DESC
                LIMIT 4
            ) result;

        SET @sqlQuery = CONCAT( 'SELECT * FROM products p WHERE p.status = 1 AND p.verified = 1 AND p.id NOT IN (', COALESCE(flashIds, '0'), ')', ' AND (', @conditions, ') AND p.deleted_at IS NULL ORDER BY p.created_at DESC LIMIT 12' );
        PREPARE stmt
        FROM
            @sqlQuery;
        EXECUTE stmt;
        DEALLOCATE PREPARE stmt;
        ELSE SELECT
            *
        FROM
            products
        WHERE
            id = - 1;

    END IF;
    WITH RankedCategories AS (
        SELECT DISTINCT
            cv.id,
            cv.NAME,
            cv.slug,
            ROW_NUMBER() OVER ( ORDER BY utc.category_count DESC, cv.`order` ) AS `order`
        FROM
            categories cv
            LEFT JOIN ( SELECT parent_category_id, user_id, SUM( category_count ) AS category_count FROM vw_user_trending_categories GROUP BY parent_category_id, user_id ) utc ON cv.id = utc.parent_category_id
            AND utc.user_id = uId
        WHERE
            cv.parent_id IS NULL
            AND cv.STATUS = 1
            AND cv.parent_disabled = 0
        ) SELECT DISTINCT
        id,
        NAME,
        slug
    FROM
        RankedCategories
    WHERE
        `order` <= 4; IF uId > 0 THEN
        SELECT
            GROUP_CONCAT(
            CAST( category_Id AS CHAR )) INTO userSlugs
        FROM
            vw_user_trending_categories
        WHERE
            user_id = uId
        ORDER BY
            category_count DESC
            LIMIT 10;
        IF
            userSlugs IS NOT NULL THEN

                SET categorySlugs = CONCAT( categorySlugs, ',', userSlugs );

        END IF;

    END IF;
    IF
        userCategoryCount < 12 THEN
        SELECT
            GROUP_CONCAT(
            CAST( item_id AS CHAR )) INTO userSlugs
        FROM
            ( SELECT id AS item_id FROM categories WHERE STATUS = 1 AND parent_disabled = 0 LIMIT 10 ) t;

        SET categorySlugs = CONCAT( categorySlugs, ',', userSlugs );

    END IF;
    WITH RECURSIVE SplitString AS (
        SELECT
            SUBSTRING_INDEX( categorySlugs, ',', 1 ) AS
        VALUE
            ,
            SUBSTRING( categorySlugs, LENGTH( SUBSTRING_INDEX( categorySlugs, ',', 1 )) + 2 ) AS rest_of_string UNION
        SELECT
            SUBSTRING_INDEX( rest_of_string, ',', 1 ) AS
        VALUE
            ,
            SUBSTRING( rest_of_string, LENGTH( SUBSTRING_INDEX( rest_of_string, ',', 1 )) + 2 ) AS rest_of_string
        FROM
            SplitString
        WHERE
            rest_of_string != ''
        ),
        RankedProducts AS (
        SELECT DISTINCT
            p.*,
            ROW_NUMBER() OVER ( PARTITION BY p.`category_id` ORDER BY p.hits DESC ) AS row_num
        FROM
            `products` p
            JOIN SplitString s ON p.`category_id` = s.`value`
            LEFT JOIN brands b ON p.brand_id = b.id
        WHERE
            p.`deleted_at` IS NULL
            AND p.`status` = 1
            AND ( b.STATUS = 1 OR b.STATUS IS NULL )
        ) SELECT
        *
    FROM
        RankedProducts
    WHERE
        row_num <= 2
    ORDER BY
        id
        LIMIT 12;
    DROP TEMPORARY TABLE
    IF
        EXISTS temp_flashSales;
END
```
