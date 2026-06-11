

<p><h1>What is CRUD?</h1></p>

<p>CRUD stands for create, read, update, and delete, which are the basic operations in any system that manages data.<br></p>

<p><h2>The create operation,</h2></p>

<p>Used to create new records in a table, this cam be achieved by using the statement "INSERT INTO"</p>

```
mysql> INSERT INTO books (id, name, published_date, description)
    -> VALUES (1, "Android Security Internals", "2014-10-14", "An In-Depth Guide to Android's Security Architecture");

```

<p><h2>The read operation,</h2></p>

<p>"SELECT" is used to read and retrieve information from a table. We can select a column or all columns from a table with SELECT.</p>

```
mysql> SELECT * FROM books;
+----+----------------------------+----------------+--------------------------------------------------------+
| id | name                       | published_date | description                                            |
+----+----------------------------+----------------+--------------------------------------------------------+
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   |
|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities |
|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     |
|  4 | Designing Secure Software  | 2021-12-21     | A Guide for Developers                                 |
|  5 | Ethical Hacking            | 2021-11-02     | A Hands-on Introduction to Breaking In                 |
|  6 | Ethical Hacking            | 2021-11-02     |                                                        |
+----+----------------------------+----------------+--------------------------------------------------------+
6 rows in set (0.00 sec)
```

<p>The "SELECT" statement is followed by an * indicating all columns should be retrieved,<br>

it is then followed by the "FROM" clause with the table name.<br>

In short, we are selecting all columns from the table books.</p>

```
ysql> SELECT name FROM books;
+----------------------------+
| name                       |
+----------------------------+
| Android Security Internals |
| Bug Bounty Bootcamp        |
| Car Hacker's Handbook      |
| Designing Secure Software  |
| Ethical Hacking            |
| Ethical Hacking            |
+----------------------------+
6 rows in set (0.00 sec)

mysql> SELECT name, description FROM books;
+----------------------------+--------------------------------------------------------+
| name                       | description                                            |
+----------------------------+--------------------------------------------------------+
| Android Security Internals | An In-Depth Guide to Android's Security Architecture   |
| Bug Bounty Bootcamp        | The Guide to Finding and Reporting Web Vulnerabilities |
| Car Hacker's Handbook      | A Guide for the Penetration Tester                     |
| Designing Secure Software  | A Guide for Developers                                 |
| Ethical Hacking            | A Hands-on Introduction to Breaking In                 |
| Ethical Hacking            |                                                        |
+----------------------------+--------------------------------------------------------+
```

<p><h2>Update Operation (UPDATE)</h2></p>

<p>The update operation modifies an existing record within a table.</p>

```
mysql> UPDATE books
    SET description = "An In-Depth Guide to Android's Security Architecture."
    WHERE id = 1;
```

<p>UPDATE specifies the table, then SET followed by column name, and WHERE which specifies our row.</p>

<p><h2>Delete Operation (DELETE)</h2></p>

<p>Removes records from a table.</p>

<p><h1>In Summary, C.R.U.D</h1></p>

<p><h2>Create (Insert)</h2></p>
<p><h2>Read (SELECT)</h2></p>
<p><h2>Update (UPDATE)</h2></p>
<p><h2>Delete (DELETE)</h2></p>
