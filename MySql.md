#### **Getting Started**
You can write two types of comments in MySQL:
> 💬 **Single-Line Comments:**
> These start with “–”. Any text that goes after the dash and till the end
> of the line will not be taken into account by the compiler.
> Example:
> ```
> -Update all:
> SELECT * FROM Movies;
> ```

> 💬 **Multi-Line Comments:**
> These start with /_ and end with _/. Again, any text that is beyond the
> slashes lines will be ignored by the compiler.
> Example:
> ```
> /*Select all the columns
> of all the records
> in the Movies table:*/
> SELECT * FROM Movies;
> ```

#### **How to Connect to MySQL**
> To start working with MySQL, you’ll need to establish an active SSH session on your server.
> ```
> mysql -u root -p
> ```
> If you didn’t set a password for your MySQL root user, you omit the -p switch.

#### **Create a new MySQL User Account**
> Next, you can create a new test user for practice. To do that, run the following command:
> ```
> CREATE USER ‘username’@’localhost’ IDENTIFIED BY ‘password’;
> ```

> If you need to delete a user later on you, use this command:
> ```
> DROP USER ‘someuser’@’localhost’;
> ```

#### **Create a New Database**
> To set up a new database use this line:
> ```
> CREATE DATABASE DbName
> ```

> You can then view all your databases with this command:
> ```
> SHOW databases;
> ```

> Later on, you can quickly navigate to a particular database using this command:
> ```
> mysql -u root -p mydatabase < DbName.sql
> ```

#### **Delete a MySQL Database**
> To get rid of a database just type:
> ```
> DROP DATABASE dbName
> ```
> If you are done for the day, just type “exit” in the command line to finish your session.

#### **Essential MySQL Commands**
**SELECT**            — choose specific data from your database\
**UPDATE**            — update data in your database\
**DELETE**            — deletes data from your database\
**INSERT INTO**       — inserts new data into a database\
**CREATE DATABASE**   — generate a new database\
**ALTER DATABASE**    — modify an existing database\
**CREATE TABLE**      — create a new table in a database\
**ALTER TABLE**       — change the selected table\
**DROP TABLE**        — delete a table\
**CREATE INDEX**     — create an index (search key for all the info stored)\
**DROP INDEX**       — delete an index

#### **Working with Tables**
Tables are the key element of MySQL databases as they let you store all the information together 
in organized rows. Each row consists of columns that feature a specified data type. You have plenty 
of options for customization using the commands below.

##### **Create a New Simple Table**
Use this command to create a new table:
```
 CREATE TABLE [IF NOT EXISTS] table_name(
  column_list
 )
```

The code snippet below features a table for a list of movies that we want to organize by different 
attributes:

```
CREATE TABLE movies(
   title VARCHAR(100),
   year VARCHAR(100),
   director VARCHAR(50),
   genre VARCHAR(20),
   rating VARCHAR(100),
 );
```

##### **View Tables**
Use the next commands to get more information about the tables stored in your database.
**show tables** — call a list of all tables associated with a database. 
**DESCRIBE table_name;** — see the columns of your table. 
**DESCRIBE table_name column_name;** — review the information of the column in your table

##### **Delete a Table**
To get rid of the table specify the table name in the following command:
```
DROP TABLE tablename;
```

#### **Working With Table Columns**
Use columns to store alike information that shares the same attribute (e.g. movie director names). 
Columns are defined by different storage types:
* **CHAR**
* **VARCHAR**
* **TEXT**
* **BLOB**
* **EUT**
* **And others.**
An in-depth overview comes in the next section!

When designing columns for your database, your goal is to select the optimal length to avoid 
wasted space and maximize performance. 
Below are the key commands for working with tables

##### **Add New Column**
```
ALTER TABLE table
ADD [COLUMN] column_name;
```

##### **Delete/Drop a Column**
```
ALTER TABLE table_name
DROP [COLUMN] column_name;
```

##### **Insert New Row**
```
INSERT INTO table_name (field1, field2, ...) VALUES (value1,
value2, ...)
```

##### **Select Data from The Row**
Specify what kind of information you want to retrieve from a certain row.
```
SELECT value1, value2 FROM field1
```
##### **Add an Additional Selection Clause**
Include an additional pointer that indicates what type of data do you need.
```
SELECT * FROM movies WHERE budget=’1’;
SELECT * FROM movies WHERE year=’2020’ AND rating=’9’;
```

##### **Delete a Row**
Use SELECT FROM syntax and WHERE clause to specify what rows to delete.
```
DELETE FROM movies WHERE budget=’1’;
```

##### **Update Rows**
Similarly, you can use different clauses to update all or specified rows in your table.
To update all rows:
```
UPDATE table_name
SET column1 = value1,
 ...;
```

To update data only in a specified set of rows you can use WHERE clause:
```
UPDATE table_name
SET column_1 = value_1,
WHERE budget=’5’
```

You can also update, select or delete rows using JOIN clause. It comes particularly handy when you
need to manipulate data from multiple tables in a single query.
Here’s how to update rows with JOIN:
```
UPDATE table_name
INNER JOIN table1 ON table1.column1 = table2.column2
SET column1 = value1,
WHERE budget=’5’
```

##### **Edit a Column**
You can alter any existing column with the following snippet:
```
ALTER TABLE movies MODIFY COLUMN number INT(3)
```

##### **Sort Entries in a Column**
You can sort the data in all columns and rows the same way you do in Excel e.g. alphabetically or
from ascending to descending value.
```
SELECT * FROM users ORDER BY last_name ASC;
SELECT * FROM users ORDER BY last_name DESC;
```

##### **Search Columns**
Here’s how you can quickly find the information you need using WHERE and LIKE syntax:
```
SELECT * FROM movies WHERE genre LIKE ‘com%’;
SELECT * FROM movies WHERE title LIKE ‘%a’;
```
You can also exclude certain items from search with NOT LIKE:
```
SELECT * FROM movies WHERE genre NOT LIKE ‘hor%’;
```

##### **Select a Range**
Or you can bring up a certain data range using the next command:
```
SELECT * FROM movies WHERE rating BETWEEN 8 AND 10;
```

##### **Concentrate Columns**
You can mash-up two or more columns together with CONCAT function:
```
SELECT CONCAT(first_name, ‘ ‘, last_name) AS ‘Name’, dept FROM
users;
```

#### **Data Types**
Data types indicate what type of information you can store in a particular column of your table.
MySQL has three main categories of data types:
* Numeric
* Text
* Date/time

##### **Numeric Data Types**
Unless programmed, the MySQL column display width will not limit the range of values that
you can store there. Also, without a numeric data type integer, your columns can display width
incorrectly if you include too wide values. To prevent that you can use the following integers to
specify the maximum allowed range of values. You can either:

* Assign a specific numeric value to the column
* Or leave an **unsigned** value.

If unsigned, the column will expand to hold the data up till a certain upper boundary range
* **BIT[(M)]** — specify a bit-value type. **M** stands for the number of bits per value, ranging from 1 to 64. The default is 1 if no T specified.
* **ZEROFILL** — auto-add UNSIGNED attribute to the column. Deprecated since the MySQL 8.0.17 version.
* **TINYINT(M)** — the smallest integer with a range of -128 to 127.
    * **TINYINT(M) [UNSIGNED]** — the range is 0 to 255.
    * **BOOL, BOOLEAN** — synonyms for TINYINT(1)
* **SMALLINT(M)** — small integer with a range of -32768 and 32767.
    * **SMALLINT(M) [UNSIGNED]** — the range is 0 to 65535.
* **MEDIUMINT(M)** — medium integer with a range of -8388608 to 8388607.
    * **MEDIUMINT(M) [UNSIGNED]** — the range is 0 to 16777215.
* **INT(M) and INTEGER (M)** — normal range integer with a range of -2147483648 to 2147483647.
    * **INT(M)[UNSIGNED] and INTEGER (M)[UNSIGNED]** — the range is 0 to 4294967295.
* **BIGINT(M)** — the largest integer with a range of -9223372036854775808 to 9223372036854775807.
    * **BIGINT(M) [UNSIGNED]** — the range is 0 to 8446744073709551615.
* **DECIMAL (M, D)** — store a double value as a string. **M** specifies the total number of digits. **D** stands for the number of digits after the decimal point. Handy for storing currency values.
    * Max number of M is 65. If omitted, the default M value is 10.
    * Max number of D is 30. If omitted, the default D is 0.
* **FLOAT (M, D)** — record an approximate number with a floating decimal point. The support for FLOAT is removed as of MySQL 8.0.17 and above.
    * Permissible values ranges are -3.402823466E+38 to -1.175494351E-38, 0, and 1.175494351E-38 to 3.402823466E+38.

##### **Blob and Text Data Types**
**BLOB** binary range enables you to store larger amounts of text data. The maximum length of a
BLOB is 65,535 (2<sup>16</sup> − 1) bytes. BLOB values are stored using a 2-byte length prefix.
**NB**: Since text data can get long, always double-check that you do not exceed the maximum
lengths. The system will typically generate a warning if you go beyond the limit. But if nonspace
characters get truncated, you may just receive an error without a warning.
* **TINYBLOB** — sets the maximum column length at 255 (2<sup>8</sup>− 1) bytes. TINYBLOB values are stored using a 1-byte length prefix.
* **MEDIUMBLOB** — sets the maximum column length at 16,777,215 (2<sup>24</sup> − 1) bytes. MEDIUMBLOB values are stored using a 3-byte length prefix.
* **LONGBLOB** — sets the maximum column length at 4,294,967,295 or 4GB (2<sup>32</sup> − 1) bytes. LONGBLOB values are stored using a 4-byte length prefix.

> [!NOTE] 
> The max length will also depend on the maximum packet size that you configure in the client/server protocol, plus available memory.

**TEXT** does the same job but holds values of smaller length. A TEXT column can have a maximum
length of **65,535 (2<sup>16</sup> − 1) characters**. However, the max length can be smaller if the value contains
multibyte characters. TEXT value is also stored using a 2-byte length prefix.

* **TINYTEXT** — store a value using a 1-byte length prefix. The maximum supported column length is 255 (2<sup>8</sup>− 1) characters.
* **MEDIUMTEXT** — store a value using a 3-byte length prefix. The maximum supported column length is 16,777,215 (2<sup>24</sup> − 1) characters.
* **LONGTEXT** — store a value using a 4-byte length prefix. The maximum supported column length is 4,294,967,295 or 4GB (2<sup>32</sup> − 1) characters.

> [!NOTE] 
> Again, the length cap will also depend on your configured maximum packet size in the client/server protocol and available memory. 

##### **Text Storage Formats**
* **CHAR** — specifies the max number of non-binary characters you can store. The range is from 0 to 255.
* **VARCHAR** — store variable-length non-binary strings. The maximum number of characters you can store is 65,535 (equal to the max row size).
    * VARCHAR values are stored as a 1-byte or 2-byte length prefix plus data, unlike CHAR values.
* **BYNARY** — store binary data in the form of byte strings. Similar to CHAR.
* **VARBYNARY** — store binary data of variable length in the form of byte strings. Similar to VARCHAR.
* **ENUM** — store permitted text values that you enumerated in the column specification whenCHAR — specifies the max number of non-binary characters you can store. The range is from 0 to 255.
    * ENUM columns can contain a maximum of 65,535 distinct elements and have > 255 unique element list definitions among its ENUM.
* **SET** — another way to store several text values that were chosen from a predefined list of values.
* **ENUM** columns can contain a maximum of 65,535 distinct elements and have > 255 unique element list definitions among its ENUM.
    * SET — another way to store several text values that were chosen from a predefined list of values.

##### **Date and Time Data Types**
As the name implies, this data type lets you store the time data in different formats.
* **DATE** — use it for values with a date part only. MySQL displays DATE values in the ‘YYYY-MMDD’ format.
    * Supported data range is ‘1000-01-01’ to ‘9999-12-31’.
* **DATETIME** — record values that have both date and time parts. The display format is ‘YYYYMM-DD hh:mm:ss’.
    * Supported data range is ‘1000-01-01 00:00:00’ to ‘9999-12-31 23:59:59’.
* **TIMESTAMP** — add more precision to record values that have both date and time parts, up till microseconds in UTC.
    * Supported data range is ‘1970-01-01 00:00:01’ UTC to ‘2038-01-19 03:14:07’ UTC.
* **TIME** — record just time values in either ‘hh:mm:ss’ or ‘hhh:mm:ss’ format. The latter can represent elapsed time and time intervals.
    * Supported data range is ‘-838:59:59’ to ‘838:59:59’.
* **YEAR** — use this 1-byte type used to store year values.
    * A 4-digit format displays YEAR values as 0000, with a range between 1901 to 2155.
    * A 2-digit format displays YEAR values as 00. The accepted range is ‘0’ to ‘99’ and MySQL will convert YEAR values in the ranges 2000 to 2069 and 1970 to 1999

#### **Working With Indexes**
**Indexes** are the core element of your database navigation. Use them to map the different types of
data in your database, so that you don’t need to parse all the records to find a match.

**NB**: You have to update an index every time you are creating, changing or deleting a record in the
table. Thus, it’s best to create indexes only when you need to and for frequently searched columns.

##### **How to Create an Index**
The basic syntax is as follows:
```
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```
You can also create a unique index — one that enforces the uniqueness of values in one or more columns.

```
CREATE UNIQUE INDEX index_name
ON table_name(index_column_1,index_column_2,...);
```

##### **How to Delete an Index in MySQL**
Use the DROP command for that:
```
DROP INDEX index_name;
```

#### **Working with Views**
A **view** is a virtual representation of an actual table that you can assemble up to your liking (before
adding the actual one to your database).

It features rows and columns, just like the real deal and can contain fields from one or more of the
real tables from your database. In short, it’s a good way to visualize and review data coming from
different tables within a single screen.

##### **How to Create a New View**
```
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
