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