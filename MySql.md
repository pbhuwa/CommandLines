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
