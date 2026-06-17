

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

<p><h2>Q1: What is the longest name based on character length in tools_db?</h2></p>

```
mysql> SELECT MAX(name) FROM hacking_tools;
+-----------------+
| MAX(name)       |
+-----------------+
| Wi-Fi Pineapple |
+-----------------+
1 row in set (0.00 sec)
```
<p>This was my first result, this is not correct, I realized I was using the wrong function. <br>

We are supposed to use the length function like so,</p>

```
mysql> SELECT LENGTH(name) FROM hacking_tools;
+--------------+
| LENGTH(name) |
+--------------+
|           12 |
|           11 |
|           15 |
|           16 |
|            8 |
|           10 |
|           10 |
|           15 |
+--------------+
8 rows in set (0.00 sec)
```

<p>Now we could view the contents of the name column and count to four, or we can add the following to our original code.</p>

<p>By using AS we can adjust the name of our length() function as a new column.</p>

```
mysql> SELECT name, LENGTH(name) AS character_count
    -> FROM hacking_tools;
+------------------+-----------------+
| name             | character_count |
+------------------+-----------------+
| Flipper Zero     |              12 |
| O.MG cables      |              11 |
| Wi-Fi Pineapple  |              15 |
| USB Rubber Ducky |              16 |
| iCopy-XS         |               8 |
| Lan Turtle       |              10 |
| Bash Bunny       |              10 |
| Proxmark 3 RDV4  |              15 |
+------------------+-----------------+
8 rows in set (0.00 sec)
```

<p><h2>A: USB Rubber Ducky</h2></p>
  
<p><h2>Q2: What is the total sum of all tools in tools_db?</h2></p>

```
mysql> SELECT SUM(amount) AS total_tools FROM hacking_tools;
+-------------+
| total_tools |
+-------------+
|        1444 |
+-------------+
1 row in set (0.00 sec)
```
<p><h2>A: 1444</h2></p>

<p><h2>Q3:Using the tools_db database, what are the tool names where the amount does not end in 0, and group the tool names concatenated by " & ".</h2></p>

```
mysql> SELECT GROUP_CONCAT(name SEPARATOR ' & ') AS tool_names
    -> FROM hacking_tools
    -> WHERE AMOUNT NOT LIKE '%0';
+-------------------------+
| tool_names              |
+-------------------------+
| Flipper Zero & iCopy-XS |
+-------------------------+
1 row in set (0.01 sec)
```
