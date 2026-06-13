

<p><h1>Logical Operators,</h1></p>

<p>Operators that test the truth of a conditon and return a boolean value of TRUE or FALSE.</p>

<p><h2>The "LIKE" operator</h2></p>

<p>Commonly used in conjunction with the "WHERE" clause to filter for specific patterns in a column.</p>

```
mysql> SELECT *
    -> FROM books
    -> WHERE description LIKE "%guide%";
+----+----------------------------+----------------+--------------------------------------------------------+--------------------+
| id | name                       | published_date | description                                            | category           |
+----+----------------------------+----------------+--------------------------------------------------------+--------------------+
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture   | Defensive Security |
|  2 | Bug Bounty Bootcamp        | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities | Offensive Security |
|  3 | Car Hacker's Handbook      | 2016-02-25     | A Guide for the Penetration Tester                     | Offensive Security |
|  4 | Designing Secure Software  | 2021-12-21     | A Guide for Developers                                 | Defensive Security |
+----+----------------------------+----------------+--------------------------------------------------------+--------------------+
```

<p>As you can tell by the returned data, all tables that contain "guide" in the description are returned.</p>

<p><h2>The "AND" operator</h2></p>

<p>Uses multiple conditions within a query and returns values only if all are TRUE.</p>

```
mysql> SELECT *
    -> FROM books
    -> WHERE category = "Offensive Security" AND name = "Bug Bounty Bootcamp";
+----+---------------------+----------------+--------------------------------------------------------+--------------------+
| id | name                | published_date | description                                            | category           |
+----+---------------------+----------------+--------------------------------------------------------+--------------------+
|  2 | Bug Bounty Bootcamp | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities | Offensive Security |
+----+---------------------+----------------+--------------------------------------------------------+--------------------+
```

<p>The above query returns a book with the name of Bug Bounty Bootcamp under the category Offensive Security.</p>

<p><h2>The "OR" operator</h2></p>

<p>Combines multiple conditions within queries and returns TRUE if one of these conditions are true.</p>

```
mysql> SELECT *
    FROM books
    WHERE name LIKE "%Android%" OR name LIKE "%iOS%"; 
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
| id | name                       | published_date | description                                          | category           |
+----+----------------------------+----------------+------------------------------------------------------+--------------------+
|  1 | Android Security Internals | 2014-10-14     | An In-Depth Guide to Android's Security Architecture | Defensive Security |
+----+----------------------------+----------------+------------------------------------------------------+--------------------+

1 row in set (0.00 sec)
```

<p>The above query returns books that have the name Adroid or IOS.</p>


<p><h2>THE "NOT" operator</h2></p>

<p>Revereses the value of the boolean operator, this allows us to exclude a condition.</p>

```
mysql> SELECT *
    -> FROM books
    -> WHERE NOT description LIKE '%guide%';
+----+-----------------+----------------+----------------------------------------+--------------------+
| id | name            | published_date | description                            | category           |
+----+-----------------+----------------+----------------------------------------+--------------------+
|  5 | Ethical Hacking | 2021-11-02     | A Hands-on Introduction to Breaking In | Offensive Security |
+----+-----------------+----------------+----------------------------------------+--------------------+
1 row in set (0.00 sec)
```

<p>Above shows results that do not contain guide in the description.</p>

<p><h2>The "BETWEEN" operator</h2></p>

<p>Allows us to test if a value exists within a defined range.</p>

```
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
| id | name                      | published_date | description                                            | category           |
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
|  2 | Bug Bounty Bootcamp       | 2021-11-16     | The Guide to Finding and Reporting Web Vulnerabilities | Offensive Security |
|  3 | Car Hacker's Handbook     | 2016-02-25     | A Guide for the Penetration Tester                     | Offensive Security |
|  4 | Designing Secure Software | 2021-12-21     | A Guide for Developers                                 | Defensive Security |
+----+---------------------------+----------------+--------------------------------------------------------+--------------------+
```


