

<p>SQL uses the english language for it's syntax, this makes it incredibly easier to learn<br>

end-users interact with SQL databases using DBMS's (Database Management Systems)</p>

<p><h1>Commands</h1></p>

<h2>Creating our first Database</h2>

```
mysql> CREATE DATABASE chicago_market;
```
<p><h2>Viewing available Databases</h2></p>

```
mysql> SHOW DATABASES;
```

<p><h2>Selecting a Database</h2></p>

```
mysql> USE chicago_market;
```

<p><h2>Removing a Database</h2></p>

```
mysql> DROP database chicago_market;
```

<p><h2>Creating tables</h2></p>

<p>You must be using the database you want to create tables within.</p>

```
mysql> USE DATABASE chicago_market;

mysql> USE chicago_market;
Database changed

mysql> CREATE TABLE inventory (
    -> food_id INT AUTO_INCREMENT PRIMARY KEY,
    -> food_name VARCHAR(255) NOT NULL,
    -> sell_by_date DATE
    -> );
Query OK, 0 rows affected (0.03 sec)
```
<p>Thee statement above will create a table named inventory, with three columns, food_id, food_name, and sell_by_date.<br>

food_id has INT(Integer) specified, meaning it should be represented as a number.<br>

"AUTO_INCREMENT" means the first entry for food_id should be one and the second should be two and so on.<br>

"PRIMARY KEY" is how we uniquely identify a food record in our table, it is also required.<br>

"VARCHAR(255)" means variable characters text, numbers, and punctation can be used with a limit of 255 characters.<br>

"NOT NULL" means the entry cannot be empty</p>

<p>We can now view our tables and columns</p>

```
mysql> SHOW TABLES;
+--------------------------+
| Tables_in_chicago_market |
+--------------------------+
| inventory                |
+--------------------------+
1 row in set (0.00 sec)
```

<p>To view columns inside a table and it's data type we use DESCRIBE or DESC</p>

```
mysql> DESC inventory;
+--------------+--------------+------+-----+---------+----------------+
| Field        | Type         | Null | Key | Default | Extra          |
+--------------+--------------+------+-----+---------+----------------+
| food_id      | int          | NO   | PRI | NULL    | auto_increment |
| food_name    | varchar(255) | NO   |     | NULL    |                |
| sell_by_date | date         | YES  |     | NULL    |                |
+--------------+--------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)
```

<p>Alerting tables,<br>

Eventually, we may need to add or remove table data.<br>

This can be done by using "ALTER" like shown below.<br>

This function allows you to rename columns, change data types, or remove a column.</p>

```
mysql> ALTER TABLE inventory
    -> ADD quantity INT;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC inventory;

mysql> DESC inventory;
+--------------+--------------+------+-----+---------+----------------+
| Field        | Type         | Null | Key | Default | Extra          |
+--------------+--------------+------+-----+---------+----------------+
| food_id      | int          | NO   | PRI | NULL    | auto_increment |
| food_name    | varchar(255) | NO   |     | NULL    |                |
| sell_by_date | date         | YES  |     | NULL    |                |
| quantity     | int          | YES  |     | NULL    |                |
+--------------+--------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)
```

<p>Similar to removing a database we can remove a table with the DROP statement.</p>

```
mysql> DROP TABLE mock_table_name;
```
  
