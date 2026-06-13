

<p><h1>Comparison Operators,</h1></p>

<p>Are used to compare values and check if they meet specified criteria.</p>

<p><h2>Equal to Operator</h2></p>

<p>The "=" Operator compares two expressesions nad determines if they are equal,<br>

Additionally it can check if a value matches another one inside the column.</p>

```
sql> SELECT * FROM books WHERE name = 'Designing Secure Software';
+----+---------------------------+----------------+------------------------+--------------------+
| id | name                      | published_date | description            | category           |
+----+---------------------------+----------------+------------------------+--------------------+
|  4 | Designing Secure Software | 2021-12-21     | A Guide for Developers | Defensive Security |
+----+---------------------------+----------------+------------------------+--------------------+
1 row in set (0.00 sec)
```

<p>A value will only be returned if an exact match corresponds with the string inside the quotes.</p>

<p><h2>Not equal to</h2></p>

<p>We can use this to exclude a value from our query.</p>

```
mysql> SELECT *
    -> FROM books
    -> WHERE name != 'Designing Secure Software';
+----+----------------------------+----------------+--------------------------------------------------------+--------------------+
| id | name                       | published_date | description                                            | category           |
+----+----------------------------+----------------+--------------------------------------------------------+--------------------+
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   | Defensive Security |
|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities | Offensive Security |
|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     | Offensive Security |
|  5 | Ethical Hacking            | 2021-11-02     | A Hands-on Introduction to Breaking In                 | Offensive Security |
+----+----------------------------+----------------+--------------------------------------------------------+--------------------+
4 rows in set (0.00 sec)
```

<p>The above query returns all values except for the name 'Designing Secure Software'</p>


<p><h2>Less than operator</h2></p>

<p>Compares if an expressions value is lesser than the provided value.</p>

```
mysql> SELECT * FROM books WHERE published_date < "2020-01-01";
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
| id | name                       | published_date | description                                          | category           |
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture | Defensive Security |
|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                   | Offensive Security |
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
```

<p><h2>Greather than operator</h2></p>

<p>Compares is an expression value is greater than the provided value</p>

```
mysql> SELECT * FROM books WHERE published_date > "2020-01-01";
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
| id | name                      | published_date | description                                            | category           |
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
|  2 | Bug Bounty Bootcamp       | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities | Offensive Security |
|  4 | Designing Secure Software | 2021-12-21     | A Guide for Developers                                 | Defensive Security |
|  5 | Ethical Hacking           | 2021-11-02     | A Hands-on Introduction to Breaking In                 | Offensive Security |
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
```

<p><h2>Less than or equal to</h2></p>

<p>if the expression with a given value is less than or equal to the provided one.</p>

```
mysql> SELECT *
    -> FROM books
    -> WHERE published_date <= "2021-01-01";
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
| id | name                       | published_date | description                                          | category           |
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture | Defensive Security |
|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                   | Offensive Security |
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
```

<p><h2>Greater than or equal to</h2></p>

<p>Compares if an expression with a given value is greater than or equal to the provided one.</p>

```
mysql> SELECT * FROM books WHERE published_date >= "2021-01-01";
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
| id | name                      | published_date | description                                            | category           |
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
|  2 | Bug Bounty Bootcamp       | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities | Offensive Security |
|  4 | Designing Secure Software | 2021-12-21     | A Guide for Developers                                 | Defensive Security |
|  5 | Ethical Hacking           | 2021-11-02     | A Hands-on Introduction to Breaking In                 | Offensive Security |
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
```

<p><h1>THM PBQ's</h1></p>

<p><h2>Q1: Using the tools_db which tool falls under the multi-tool category and is useful for pentesters and geeks?</h2></p>

```
mysql> USE tools_db;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> SHOW tables;
+--------------------+
| Tables_in_tools_db |
+--------------------+
| hacking_tools      |
+--------------------+
1 row in set (0.00 sec)

mysql> SELECT * 
    -> FROM hacking_tools
    -> WHERE category LIKE '%pentesters and geeks%';
Empty set (0.00 sec)

mysql> SELECT * FROM hacking_tools WHERE description LIKE '%pentesters and geek
s%';
+----+--------------+------------+-------------------------------------------------------------------+--------+
| id | name         | category   | description                                                       | amount |
+----+--------------+------------+-------------------------------------------------------------------+--------+
|  1 | Flipper Zero | Multi-tool | A portable multi-tool for pentesters and geeks in a toy-like form |    169 |
+----+--------------+------------+-------------------------------------------------------------------+--------+
1 row in set (0.00 sec)

```

<p>Initially I accidentally searched for the description using the category column name.<br>

Once I realized this I queried the correct column and got the answer which was the flipper-zero. </p>

<p><h2>Q2: Using the tools_db database, what is the category of tools with an amount greater than or equal to 300?</h2></p>

<p>I wasn't sure what the row names could be here, I assumed it would be "amount" like referenced in the question, but I double checked using DESC to make sure.<br>

I accidentally added my column into table category for my FROM clause which returned an error "tale 'tools.db.category' doesn't exist.<br>

I modified my query by changing the from to the table name, then appended the row to the end.</p>
 
```
mysql> DESC hacking_tools
    -> ;
+-------------+-------------+------+-----+---------+----------------+
| Field       | Type        | Null | Key | Default | Extra          |
+-------------+-------------+------+-----+---------+----------------+
| id          | int         | NO   | PRI | NULL    | auto_increment |
| name        | varchar(50) | NO   |     | NULL    |                |
| category    | varchar(50) | NO   |     | NULL    |                |
| description | text        | YES  |     | NULL    |                |
| amount      | int         | NO   |     | NULL    |                |
+-------------+-------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> SELECT *
    -> FROM category 
    -> WHERE amount >= 300;
ERROR 1146 (42S02): Table 'tools_db.category' doesn't exist
mysql> SELECT * FROM hacking_tools  WHERE amount >= 300;
+----+-----------------+--------------+---------------------------------------------------------------------+--------+
| id | name            | category     | description                                                         | amount |
+----+-----------------+--------------+---------------------------------------------------------------------+--------+
|  5 | iCopy-XS        | RFID cloning | A tool used for reading and cloning RFID cards for security testing |    375 |
|  8 | Proxmark 3 RDV4 | RFID cloning | A powerful RFID tool for reading, writing, and analyzing RFID tags  |    300 |
+----+-----------------+--------------+---------------------------------------------------------------------+--------+
2 rows in set (0.00 sec)

```

<p><h2>A: RFID cloning</h2></p>

<p><h2>Q3: Using the tools_db database, which tool falls under the Network Intelligence category with an amount less than 100?</h2></p>

<p>Because of the previous questions I know where I'm meant to be querying.<br>

I am going to combine LIKE and AND to return the exact result the question is looking for.</p>

```
mysql> 
mysql> SELECT *
    -> FROM hacking_tools
    -> WHERE category = 'Network intelligence'
    -> AND amount < 100;
+----+------------+----------------------+--------------------------------------------------------------------+--------+
| id | name       | category             | description                                                        | amount |
+----+------------+----------------------+--------------------------------------------------------------------+--------+
|  6 | Lan Turtle | Network intelligence | A covert tool for remote access and network intelligence gathering |     80 |
+----+------------+----------------------+--------------------------------------------------------------------+--------+
```

<p>A: Lan Turtle</p>

<p>My query worked flawlessy.</p>


