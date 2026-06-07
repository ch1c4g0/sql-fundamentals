

<p><h1>What are databases?</h1></p>

<p>Databases are everywhere, this text you are reading is being stored in a database.<br>
Simply put, databases are an organised collection of structured information or data that is easily accessible and can be manipulated or analysed.<br>
Data stored in databases can vary from, User authentication, user-generated data(content), or even watch history.</p>

<p><h1>Different types of databases</h1></p>

<p><h2>Relational databases</h2></p>

<p>Relational databases store structured data, meaning the database stores data in a consistent format.<br>
Structured data is stored in rows and columns inside a table. Relations can be made between two or more tables which is why they are called relational databases.</p>

<p>Example relational database structure,</p>

```
+----+----------------+----------------------+------------+----------+
| ID | Name           | Email                | Join Date  | Status   |
+----+----------------+----------------------+------------+----------+
|  1 | Alice Johnson  | alice@example.com    | 2024-01-15 | Active   |
|  2 | Bob Smith      | bob@example.com      | 2024-02-03 | Active   |
|  3 | Carol Davis    | carol@example.com    | 2024-03-21 | Inactive |
|  4 | David Wilson   | david@example.com    | 2024-04-10 | Pending  |
|  5 | Emma Brown     | emma@example.com     | 2024-05-18 | Active   |
+----+----------------+----------------------+------------+----------+
```

<p><h2>Non-relational databases</h2></p>

<p>Data is stored in a non-table format. This is great for data that doesn't follow a consistent format but needs to be collected and organized in the same place.</p>

<p>Example non-relational format,</p>

```
 {
    _id: ObjectId("4556712cd2b2397ce1b47661"),
    name: { first: "Thomas", last: "Anderson" },
    date_of_birth: new Date('Sep 2, 1964'),
    occupation: [ "The One"],
    steps_taken : NumberLong(4738947387743977493)
}
```

<p><h1>Tables, Rows, and Columns</h1></p>

<p>All data stored in a relational database will be stored in a table, within table will be columns, columns are the types of data you are storing ie. first name, last name, phone number, ect. The different entries within your columns are called Rows.</p>


<p><h1>Primary and Foreign Keys</h1></p>

<p>Primary and Foreign Keys form relations between two different tables.</p>

<p><h2>Primary Keys</h2></p>

<p>They are used to ensure the data can be identified when stored in a table, this value is not repeated by any other record in that table.</p>

<p><h2>Foreign Keys</h2></p>

<p>A column or columns that also exist in another table within the database, this provides a link between te two databases.</p>


