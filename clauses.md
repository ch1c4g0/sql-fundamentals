
<p><h1>What is a clause?</h1></p>

<p>A clause is a statement that specifies the criteria of the data being manipulated, usually by a statement.<br>

They define the type of data and how it should be retrieved / sorted.<br>

You may recall we previously used the "FROM" clause to specify the table we are accessing with our "WHERE" statement.</p>

<p><h1>The other clauses,</h1></p>

<p><h2>DISTINCT, GROUP BY, ORDER BY, and HAVING</h2></p>

<p><h3>DISTINCT,</h3></p>

<p>This clause is used to avoid duplicate records when performing a query, it will return only unique values.<br>

In the example below we query the "books table" and rows 5 and 6 appear to have duplicate data, a perfect use case for DISTINCT.</p>

```
mysql> SELECT * FROM books
    -> ;
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
```

```
mysql> SELECT DISTINCT name FROM books;
+----------------------------+
| name                       |
+----------------------------+
| Android Security Internals |
| Bug Bounty Bootcamp        |
| Car Hacker's Handbook      |
| Designing Secure Software  |
| Ethical Hacking            |
+----------------------------+
5 rows in set (0.00 sec)
```

<p><h3>GROUP BY,</h3></p>

<p>This clause aggregates data from multiple records and groups the query results into columns, helpful for aggregating functions.<br>

In the following example results are regrouped by the result of the "COUNT" function.<br>

GROUP BY and ORDER BY are most commonly used with aggregate functions like to summarize and rank data.</p>

```
The primary functions used are:
SUM(): Calculates the total value for each group.
COUNT(): Returns the number of rows or non-null values in a group.
AVG(): Computes the mathematical average of a numeric column per group.
MAX() & MIN(): Finds the highest and lowest values within a group, respectivel
```

```
mysql> SELECT name, COUNT(*)
    -> FROM books
    -> GROUP BY name;
+----------------------------+----------+
| name                       | COUNT(*) |
+----------------------------+----------+
| Android Security Internals |        1 |
| Bug Bounty Bootcamp        |        1 |
| Car Hacker's Handbook      |        1 |
| Designing Secure Software  |        1 |
| Ethical Hacking            |        2 |
+----------------------------+----------+
5 rows in set (0.01 sec)
```

<p><h3>ORDER BY</h3></p>

<p>Can be used to sort the records returned by a query in ascending or descending order.<br>

Functions like ASC and DESC can help us accomplish this.</p>

<p><h4>Ascending Order</h4></p>

```
mysql> SELECT *
    -> FROM books
    -> ORDER BY published_date ASC;
+----+----------------------------+----------------+--------------------------------------------------------+
| id | name                       | published_date | description                                            |
+----+----------------------------+----------------+--------------------------------------------------------+
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   |
|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     |
|  5 | Ethical Hacking            | 2021-11-02     | A Hands-on Introduction to Breaking In                 |
|  6 | Ethical Hacking            | 2021-11-02     |                                                        |
|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities |
|  4 | Designing Secure Software  | 2021-12-21     | A Guide for Developers                                 |
+----+----------------------------+----------------+--------------------------------------------------------+
6 rows in set (0.00 sec)
```

<p>If you look back at previous examples, you'll notice that the data is now sorted differently than before.<br>

It's important to note that ASC stands for ascending, which is why the columns look the way they do.<br>

Ascending = Oldest (Top) - Newest (Bottom)</p>

<p><h4>Descending Order</h4></p>

```
mysql> SELECT * FROM books ORDER BY published_date DESC;
+----+----------------------------+----------------+--------------------------------------------------------+
| id | name                       | published_date | description                                            |
+----+----------------------------+----------------+--------------------------------------------------------+
|  4 | Designing Secure Software  | 2021-12-21     | A Guide for Developers                                 |
|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities |
|  5 | Ethical Hacking            | 2021-11-02     | A Hands-on Introduction to Breaking In                 |
|  6 | Ethical Hacking            | 2021-11-02     |                                                        |
|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     |
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   |
+----+----------------------------+----------------+--------------------------------------------------------+
6 rows in set (0.00 sec)
```

<p><h3>HAVING,</h3></p>

<p>This clause is used with other clauses to filter groups or results of records based on a condition.<br>
  
in the case of GROUP BY it evaluates the condition to TRUE or FALSE, unlike WHERE, HAVING filters the results after aggregation is performed.</p>

```
mysql> SELECT name, COUNT(*)
    ->     FROM books
    ->     GROUP BY name
    ->     HAVING name LIKE '%Hack%';
+-----------------------+----------+
| name                  | COUNT(*) |
+-----------------------+----------+
| Car Hacker's Handbook |        1 |
| Ethical Hacking       |        2 |
+-----------------------+----------+
2 rows in set (0.01 sec)
```

<p>In the example above, we can observe that the query returns the books with the names that contain the word hack and the proper count, as we learned before.</p>

<p><h1>Performance Questions,</h1></p>

<p><h2>using the tools_db database, what is the total number of distinct categories in the hacking_tools table?</h2></p>

```
mysql> SELECT DISTINCT category FROM hacking_tools;
+----------------------+
| category             |
+----------------------+
| Multi-tool           |
| Cable-based attacks  |
| Wi-Fi hacking        |
| USB attacks          |
| RFID cloning         |
| Network intelligence |
+----------------------+
6 rows in set (0.00 sec)
```

<p><h2>ANSWER: 6</h2></p>

<p><h2>using the tools_db database, what is the first tool (by name) in ascending order from the hacking_tools table?</h2></p>

```
mysql> SELECT name FROM hacking_tools ORDER BY name ASC;

+------------------+
| name             |
+------------------+
| Bash Bunny       |
| Flipper Zero     |
| iCopy-XS         |
| Lan Turtle       |
| O.MG cables      |
| Proxmark 3 RDV4  |
| USB Rubber Ducky |
| Wi-Fi Pineapple  |
+------------------+
8 rows in set (0.00 sec)
```

<p><h2>ANSWER: Bash Bunny</h2></p>

<p><h2>using the tools_db database, what is the first tool (by name) in descending order from the hacking_tools table?</h2></p>

```
mysql> SELECT name FROM hacking_tools ORDER BY name DESC;
+------------------+
| name             |
+------------------+
| Wi-Fi Pineapple  |
| USB Rubber Ducky |
| Proxmark 3 RDV4  |
| O.MG cables      |
| Lan Turtle       |
| iCopy-XS         |
| Flipper Zero     |
| Bash Bunny       |
+------------------+
8 rows in set (0.00 sec)
```

<p><h2>ANSWER: Wi-Fi Pineapple</h2></p>
