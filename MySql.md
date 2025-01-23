# MySQL Guide

## Table of Contents
1. [Getting Started](#getting-started)
2. [How to Connect to MySQL](#how-to-connect-to-mysql)
3. [Create a New MySQL User Account](#create-a-new-mysql-user-account)
4. [Create a New Database](#create-a-new-database)
5. [Delete a MySQL Database](#delete-a-mysql-database)
6. [Essential MySQL Commands](#essential-mysql-commands)
7. [Working with Tables](#working-with-tables)
   - [Create a New Simple Table](#create-a-new-simple-table)
   - [View Tables](#view-tables)
   - [Delete a Table](#delete-a-table)
8. [Working with Table Columns](#working-with-table-columns)
   - [Add New Column](#add-new-column)
   - [Delete/Drop a Column](#delete-drop-a-column)
   - [Insert New Row](#insert-new-row)
   - [Select Data from The Row](#select-data-from-the-row)
   - [Add an Additional Selection Clause](#add-an-additional-selection-clause)
   - [Delete a Row](#delete-a-row)
   - [Update Rows](#update-rows)
   - [Edit a Column](#edit-a-column)
   - [Sort Entries in a Column](#sort-entries-in-a-column)
   - [Search Columns](#search-columns)
   - [Select a Range](#select-a-range)
   - [Concatenate Columns](#concatenate-columns)
9. [Introduction to Data Types](#introduction-to-data-types)
10. [Numeric Data Types](#numeric-data-types)
   - [BIT](#bit)
   - [ZEROFILL](#zerofill)
   - [Integer Types](#integer-types)
   - [Floating-Point Types](#floating-point-types)
11. [BLOB and TEXT Data Types](#blob-and-text-data-types)
   - [BLOB Data Types](#blob-data-types)
   - [TEXT Data Types](#text-data-types)
   - [Text Storage Formats](#text-storage-formats)
12. [Date and Time Data Types](#date-and-time-data-types)
13. [Working With Indexes](#working-with-indexes)  
   - [What are Indexes?](#what-are-indexes)  
   - [How to Create an Index](#how-to-create-an-index)  
   - [How to Delete an Index](#how-to-delete-an-index)  
14. [Working With Views](#working-with-views)  
   - [What are Views?](#what-are-views)  
   - [How to Create a New View](#how-to-create-a-new-view)  
   - [How to Update a View](#how-to-update-a-view)  
   - [How to Rename a View](#how-to-rename-a-view)  
   - [How to Show All Views](#how-to-show-all-views)  
   - [How to Delete a View](#how-to-delete-a-view)  
15. [Working With Triggers](#working-with-triggers)  
   - [What are Triggers?](#what-are-triggers)  
   - [How to Create a Trigger](#how-to-create-a-trigger)  
   - [How to Review Triggers](#how-to-review-triggers)  
   - [How to Delete a Trigger](#how-to-delete-a-trigger)  
16. [Stored Procedures for MySQL](#stored-procedures-for-mysql)  
   - [What are Stored Procedures?](#what-are-stored-procedures)  
   - [How to Create a Stored Procedure](#how-to-create-a-stored-procedure)  
   - [How to Review Stored Procedures](#how-to-review-stored-procedures)  
   - [How to Delete a Stored Procedure](#how-to-delete-a-stored-procedure)  
17. [Logical Operators](#logical-operators)  
   - [Overview of Logical Operators](#overview-of-logical-operators)  
   - [Special Operators](#special-operators)  
18. [Aggregate Functions](#aggregate-functions)  
   - [Overview](#overview)  
   - [MIN Function](#min-function)  
   - [MAX Function](#max-function)  
   - [COUNT Function](#count-function)  
   - [AVG Function](#avg-function)  
   - [SUM Function](#sum-function)  
19. [SQL Database Backup and Restore Commands](#sql-database-backup-and-restore-commands)  
   - [Backup Commands](#backup-commands)  
   - [Restore Commands](#restore-commands)  
   - [Import Database Command](#import-database-command)  
20. [Additional MySQL Commands](#additional-mysql-commands)  

---

## Getting Started
You can write two types of comments in MySQL:

> 💬 **Single-Line Comments:**  
These start with “–”. Any text that goes after the dash and till the end of the line will not be taken into account by the compiler.  
Example:
```
-- Update all:
SELECT * FROM Movies;
```

> 💬 **Multi-Line Comments:**  
These start with `/*` and end with `*/`. Any text that is beyond the slashes lines will be ignored by the compiler.  
Example:
```
/* Select all the columns
of all the records
in the Movies table: */
SELECT * FROM Movies;
```

---

## How to Connect to MySQL
To start working with MySQL, you’ll need to establish an active SSH session on your server.
```
mysql -u root -p
```
If you didn’t set a password for your MySQL root user, you omit the `-p` switch.

---

## Create a New MySQL User Account
Next, you can create a new test user for practice. To do that, run the following command:
```
CREATE USER ‘username’@’localhost’ IDENTIFIED BY ‘password’;
```

If you need to delete a user later on you, use this command:
```
DROP USER ‘someuser’@’localhost’;
```

---

## Create a New Database
To set up a new database, use this line:
```
CREATE DATABASE DbName;
```

You can then view all your databases with this command:
```
SHOW databases;
```

Later on, you can quickly navigate to a particular database using this command:
```
mysql -u root -p mydatabase < DbName.sql
```

---

## Delete a MySQL Database
To get rid of a database, just type:
```
DROP DATABASE dbName;
```

If you are done for the day, just type “exit” in the command line to finish your session.

---

## Essential MySQL Commands
- **SELECT** — choose specific data from your database
- **UPDATE** — update data in your database
- **DELETE** — deletes data from your database
- **INSERT INTO** — inserts new data into a database
- **CREATE DATABASE** — generate a new database
- **ALTER DATABASE** — modify an existing database
- **CREATE TABLE** — create a new table in a database
- **ALTER TABLE** — change the selected table
- **DROP TABLE** — delete a table
- **CREATE INDEX** — create an index (search key for all the info stored)
- **DROP INDEX** — delete an index

---

## Working with Tables
Tables are the key element of MySQL databases as they let you store all the information together in organized rows. Each row consists of columns that feature a specified data type. You have plenty of options for customization using the commands below.

### Create a New Simple Table
Use this command to create a new table:
```
CREATE TABLE [IF NOT EXISTS] table_name(
  column_list
);
```

The code snippet below features a table for a list of movies that we want to organize by different attributes:
```
CREATE TABLE movies(
   title VARCHAR(100),
   year VARCHAR(100),
   director VARCHAR(50),
   genre VARCHAR(20),
   rating VARCHAR(100)
);
```

### View Tables
Use the next commands to get more information about the tables stored in your database.
- `show tables` — call a list of all tables associated with a database.
- `DESCRIBE table_name;` — see the columns of your table.
- `DESCRIBE table_name column_name;` — review the information of the column in your table.

### Delete a Table
To get rid of the table, specify the table name in the following command:
```
DROP TABLE tablename;
```
```

```markdown
## Working With Table Columns
Use columns to store alike information that shares the same attribute (e.g., movie director names).  
Columns are defined by different storage types:
- **CHAR**
- **VARCHAR**
- **TEXT**
- **BLOB**
- **ENUM**
- **And others.**

An in-depth overview comes in the next section!

When designing columns for your database, your goal is to select the optimal length to avoid wasted space and maximize performance. Below are the key commands for working with tables.

### Add New Column
```
ALTER TABLE table
ADD [COLUMN] column_name;
```

### Delete/Drop a Column
```
ALTER TABLE table_name
DROP [COLUMN] column_name;
```

### Insert New Row
```
INSERT INTO table_name (field1, field2, ...) 
VALUES (value1, value2, ...);
```

### Select Data from The Row
Specify what kind of information you want to retrieve from a certain row.
```
SELECT value1, value2 
FROM field1;
```

### Add an Additional Selection Clause
Include an additional pointer that indicates what type of data you need.
```
SELECT * 
FROM movies 
WHERE budget='1';

SELECT * 
FROM movies 
WHERE year='2020' AND rating='9';
```

### Delete a Row
Use `DELETE FROM` syntax and `WHERE` clause to specify which rows to delete.
```
DELETE FROM movies 
WHERE budget='1';
```

### Update Rows
You can update all or specified rows in your table using the following commands:

To update all rows:
```
UPDATE table_name
SET column1 = value1,
    ...;
```

To update data only in a specified set of rows, you can use the `WHERE` clause:
```
UPDATE table_name
SET column_1 = value_1
WHERE budget='5';
```

You can also update, select, or delete rows using the `JOIN` clause. It’s especially useful when you need to manipulate data from multiple tables in a single query. Here’s how to update rows with `JOIN`:
```
UPDATE table_name
INNER JOIN table1 ON table1.column1 = table2.column2
SET column1 = value1
WHERE budget='5';
```

### Edit a Column
You can alter any existing column with the following snippet:
```
ALTER TABLE movies 
MODIFY COLUMN number INT(3);
```

### Sort Entries in a Column
You can sort the data in all columns and rows the same way you do in Excel, e.g., alphabetically or from ascending to descending value:
```
SELECT * 
FROM users 
ORDER BY last_name ASC;

SELECT * 
FROM users 
ORDER BY last_name DESC;
```

### Search Columns
Here’s how you can quickly find the information you need using `WHERE` and `LIKE` syntax:
```
SELECT * 
FROM movies 
WHERE genre LIKE 'com%';

SELECT * 
FROM movies 
WHERE title LIKE '%a';
```
You can also exclude certain items from the search with `NOT LIKE`:
```
SELECT * 
FROM movies 
WHERE genre NOT LIKE 'hor%';
```

### Select a Range
You can bring up a certain data range using the next command:
```
SELECT * 
FROM movies 
WHERE rating BETWEEN 8 AND 10;
```

### Concatenate Columns
You can merge two or more columns together with the `CONCAT` function:
```
SELECT CONCAT(first_name, ' ', last_name) AS 'Name', dept 
FROM users;
```
## Introduction to Data Types
Data types indicate what type of information you can store in a particular column of your table.  
MySQL has three main categories of data types:
- **Numeric**
- **Text**
- **Date/Time**

---

## Numeric Data Types

### BIT
- **BIT[(M)]**: Specifies a bit-value type.  
  - **M**: Number of bits per value (range: 1–64).  
  - Default: **M = 1** if not specified.

### ZEROFILL
- Automatically adds the **UNSIGNED** attribute to a column.  
- **Deprecated** since MySQL 8.0.17.

### Integer Types
- **TINYINT(M)**: Smallest integer.  
  - Range: -128 to 127.  
  - **UNSIGNED**: Range: 0 to 255.  
  - **BOOL**/**BOOLEAN**: Synonyms for **TINYINT(1)**.
  
- **SMALLINT(M)**: Small integer.  
  - Range: -32,768 to 32,767.  
  - **UNSIGNED**: Range: 0 to 65,535.

- **MEDIUMINT(M)**: Medium integer.  
  - Range: -8,388,608 to 8,388,607.  
  - **UNSIGNED**: Range: 0 to 16,777,215.

- **INT(M)** or **INTEGER(M)**: Normal integer.  
  - Range: -2,147,483,648 to 2,147,483,647.  
  - **UNSIGNED**: Range: 0 to 4,294,967,295.

- **BIGINT(M)**: Largest integer.  
  - Range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.  
  - **UNSIGNED**: Range: 0 to 18,446,744,073,709,551,615.

### Floating-Point Types
- **DECIMAL(M, D)**: Stores a double value as a string.  
  - **M**: Total number of digits (max: 65, default: 10).  
  - **D**: Number of digits after the decimal point (max: 30, default: 0).

- **FLOAT(M, D)**: Approximate number with a floating decimal point.  
  - **Deprecated** since MySQL 8.0.17.  
  - Range: -3.402823466E+38 to 3.402823466E+38.

---

## BLOB and TEXT Data Types

### BLOB Data Types
- **TINYBLOB**: Max length: 255 bytes. Stored with a 1-byte length prefix.  
- **BLOB**: Max length: 65,535 bytes. Stored with a 2-byte length prefix.  
- **MEDIUMBLOB**: Max length: 16,777,215 bytes. Stored with a 3-byte length prefix.  
- **LONGBLOB**: Max length: 4,294,967,295 bytes. Stored with a 4-byte length prefix.

### TEXT Data Types
- **TINYTEXT**: Max length: 255 characters. Stored with a 1-byte length prefix.  
- **TEXT**: Max length: 65,535 characters. Stored with a 2-byte length prefix.  
- **MEDIUMTEXT**: Max length: 16,777,215 characters. Stored with a 3-byte length prefix.  
- **LONGTEXT**: Max length: 4,294,967,295 characters. Stored with a 4-byte length prefix.

> **Note**: Length limitations also depend on packet size and available memory.

### Text Storage Formats
- **CHAR**: Fixed-length strings (max: 255 characters).  
- **VARCHAR**: Variable-length strings (max: 65,535 characters).  
- **BINARY**/**VARBINARY**: Binary equivalents of **CHAR**/**VARCHAR**.  
- **ENUM**: Predefined list of permitted values (max: 65,535 distinct values).  
- **SET**: Store multiple predefined text values.

---

## Date and Time Data Types
- **DATE**: Stores date values (format: `YYYY-MM-DD`).  
  - Range: `1000-01-01` to `9999-12-31`.

- **DATETIME**: Stores date and time values (format: `YYYY-MM-DD hh:mm:ss`).  
  - Range: `1000-01-01 00:00:00` to `9999-12-31 23:59:59`.

- **TIMESTAMP**: UTC-based date and time values (up to microseconds).  
  - Range: `1970-01-01 00:00:01` UTC to `2038-01-19 03:14:07` UTC.

- **TIME**: Time values (formats: `hh:mm:ss` or `hhh:mm:ss`).  
  - Range: `-838:59:59` to `838:59:59`.

- **YEAR**: Year values in 2-digit or 4-digit formats.  
  - Range: `1901` to `2155` (4-digit).  
  - Range: `0` to `99` (2-digit, auto-converted by MySQL).

```markdown

---

## Working With Indexes

### What are Indexes?
**Indexes** are a crucial element for efficient database navigation. They allow you to quickly locate rows in a table without scanning the entire table.  

> **Note:** Indexes require updates whenever records in the table are created, modified, or deleted. Therefore, use indexes sparingly and only for columns that are frequently queried.

---

### How to Create an Index
To create an index on one or more columns, use the following syntax:
```
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```

#### Create a Unique Index
A **unique index** ensures that the indexed columns contain only unique values:
```
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
```

---

### How to Delete an Index
To delete an index, use the `DROP` command:
```
DROP INDEX index_name;
```

---

## Working With Views

### What are Views?
A **view** is a virtual table that represents the result of a SQL query. Views can:
- Combine data from multiple tables.
- Simplify complex queries by abstracting them into a single object.
- Always display up-to-date data since the database engine recreates the view each time it is queried.

---

### How to Create a New View
To create a view, use the following syntax:
```
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

---

### How to Update a View
A view always reflects the latest data. To refresh or modify a view, use:
```
CREATE OR REPLACE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

---

### How to Rename a View
To rename a view for better organization:
```
RENAME TABLE view_name TO new_view_name;
```

---

### How to Show All Views
To list all views in the database:
```
SHOW FULL TABLES
WHERE table_type = 'VIEW';
```

---

### How to Delete a View
To delete a single view, use:
```
DROP VIEW [IF EXISTS] view_name;
```

To delete multiple views at once:
```
DROP VIEW [IF EXISTS] view1, view2, ...;
```
```markdown

## Working With Triggers

### What are Triggers?
A **trigger** is a database object associated with a table that activates when specific events (e.g., row inserts, updates, or deletions) occur.

> **Example Use Cases:**
> - Automatically update a timestamp column on data modification.
> - Enforce complex business rules at the database level.

---

### How to Create a Trigger
To create a trigger that runs **BEFORE** or **AFTER** an event like `INSERT`, `UPDATE`, or `DELETE`, use:
```
CREATE TRIGGER trigger_name
{BEFORE | AFTER} {INSERT | UPDATE | DELETE}
ON table_name FOR EACH ROW
trigger_body;
```

---

### How to Review Triggers
You can view all active triggers in your database using the `SHOW TRIGGERS` command:
```
SHOW TRIGGERS
[{FROM | IN} database_name]
[LIKE 'pattern' | WHERE search_condition];
```

---

### How to Delete a Trigger
To remove a trigger:
```
DROP TRIGGER [IF EXISTS] trigger_name;
```

---

## Stored Procedures for MySQL

### What are Stored Procedures?
**Stored procedures** are reusable SQL snippets stored in your database. They simplify repetitive tasks and improve code reusability.

---

### How to Create a Stored Procedure
#### Simple Stored Procedure:
```
CREATE PROCEDURE procedure_name
AS
sql_statement;
```

#### Stored Procedure with Parameters:
```
CREATE PROCEDURE SelectAllMovies(IN Title VARCHAR(30))
BEGIN
  SELECT * FROM Movies WHERE Title = Title;
END;
```

---

### How to Review Stored Procedures
To list all stored procedures in your database:
```
SHOW PROCEDURE STATUS
[LIKE 'pattern' | WHERE search_condition];
```

---

### How to Delete a Stored Procedure
To delete a stored procedure:
```
DROP PROCEDURE [IF EXISTS] procedure_name;
```

---

## Logical Operators

### Overview of Logical Operators
Logical operators help you combine conditions in `WHERE` clauses for advanced queries:
- **`AND`**: Select records that meet all specified conditions.
- **`OR`**: Select records that meet at least one condition.
- **`NOT`**: Exclude records that meet a specific condition.

---

### Special Operators
- **`BETWEEN`**: Select records within a range.
  ```
  SELECT * FROM table_name WHERE column_name BETWEEN value1 AND value2;
  ```
- **`LIKE`**: Search for patterns in text.
  ```
  SELECT * FROM table_name WHERE column_name LIKE 'pattern%';
  ```
- **`IS NULL`**: Find records with `NULL` values.
  ```
  SELECT * FROM table_name WHERE column_name IS NULL;
  ```
- **`IN`**: Check if a value matches any value in a list.
  ```
  SELECT * FROM table_name WHERE column_name IN (value1, value2, ...);
  ```
- **`ALL`**: Compare a value to all values in a list.
  ```
  SELECT * FROM table_name WHERE column_name > ALL (subquery);
  ```
- **`ANY`**: Compare a value to any value in a list.
  ```
  SELECT * FROM table_name WHERE column_name > ANY (subquery);
  ```
- **`EXISTS`**: Check if a subquery returns any rows.
  ```
  SELECT * FROM table_name WHERE EXISTS (subquery);
  ```

```markdown

---

## Aggregate Functions

### Overview
**Aggregate functions** perform calculations on a set of values and return a single result. They are often used with **GROUP BY** and **HAVING** clauses to organize data.

---

### MIN Function
Returns the smallest value in a column:
```
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

---

### MAX Function
Returns the largest value in a column:
```
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

---

### COUNT Function
Counts the number of rows that match a specified condition:
```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

---

### AVG Function
Calculates the average value of a numeric column:
```
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

---

### SUM Function
Calculates the total sum of a numeric column:
```
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

---

## SQL Database Backup and Restore Commands

### Backup Commands
To create a backup of your database:
```
mysqldump -u Username -p dbNameYouWant > databasename_backup.sql
```

---

### Restore Commands
To restore a database from a backup file:
```
mysql -u Username -p dbNameYouWant < databasename_backup.sql
```

---

### Import Database Command
To import an existing SQL file into your database:
```
SOURCE C:\Users\UserName\Downloads\dbName.sql
```

---

## Additional MySQL Commands

### Viewing Tables
Show all tables in the current database:
```
SHOW TABLES;
```

### Viewing Columns
Show column details for a specific table:
```
DESCRIBE table_name;
```

### Viewing Indexes
Display all indexes of a table:
```
SHOW INDEX FROM table_name;
```

### Display Current Database
Check the name of the currently selected database:
```
SELECT DATABASE();
```

This Markdown provides a comprehensive guide to get started with MySQL, including essential commands and operations on databases and tables.