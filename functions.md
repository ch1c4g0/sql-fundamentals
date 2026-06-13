

<p><h1>What are the purpose of functions?</h1></p>

<p>Functions can help us streamline queries and operations and manipulate data.</p>

<p><h2>String Functions</h2></p>

<p>Perform operations on a string, returning an associated value.</p>

<p><h3>CONCAT()</h3></p>

<p>Used to add two or more strings together<br>

It is useful to combine text from different columns.</p>

```
mysql> SELECT CONCAT(name, " is a type of ", category, " book.") AS book_info FROM books;
+------------------------------------------------------------------+
| book_info                                                         |
+------------------------------------------------------------------+
| Android Security Internals is a type of Defensive Security book. |
| Bug Bounty Bootcamp is a type of Offensive Security book.        |
| Car Hacker's Handbook is a type of Offensive Security book.      |
| Designing Secure Software is a type of Defensive Security book.  |
| Ethical Hacking is a type of Offensive Security book.            |
+------------------------------------------------------------------+

5 rows in set (0.00 sec)
```

<p>There are many other functions that I will not describe in detail here.<br>

GROUP_CONCAT(), SUBSTRING(), LENGTH(), COUNT(), SUM(), MAX(), MIN()</p>
