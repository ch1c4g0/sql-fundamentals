

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

<p><h2>Not Equal To</h2></p>

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


