# Course--MySQL-Database-Tutorial

Referenced link: [thenewboston - MySQL Database Tutorial](https://www.youtube.com/playlist?list=PL32BC9C878BA72085)

## Introduction to Databases

### What is a database?

Database is a collection of data. In which we can make "tables". table store some related information.

#### table

-   table are made of "column" and "rows".
-   Column are like categories
-   Each entry is on a separate row.

##### Primary Keys

-   all tables should have "primary keys".
-   no rows can have same primary key

##### Table demo

| ID  | Name   | Age |
| :-- | :----- | :-- |
| 1   | User 1 | 20  |
| 2   | User 2 | 22  |
| 3   | User 3 | 28  |

### what is SQL?

SQL stands for Structured Query Language, which is a computer language for storing, manipulating and retrieving data stored in a relational database.

---

## SQL Query

Standers: All letters must be in capital.
only thing that's not going to be in capital letters is table name and column names those are going to be in lowercase but in this language the keywords those are going to be typed in all capital letters by standard.

<br />

### Show all databases from your server

We will use this command to show the list of databases.

```
SHOW DATABASES
```

| Database           |
| :----------------- |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| test               |
| youtube            |

<br />

### Show all tables from a database

Returns the table from a specific database.

```
SHOW TABLES
```

| Tables_in_youtube |
| :---------------- |
| customers         |

<br />

### Show all headings from a database

Table name must be in lowercase. When ever do you run this command then return the names of columns i.e. `id`, `name`, etc and some other information. `PRI` mean this a primary key.

```
SHOW COLUMNS FROM customers
```

| Field   | Type        | Null | Key | Default | Extra |
| :------ | :---------- | :--- | :-- | :------ | :---- |
| id      | int(11)     | NO   | PRI | NULL    |       |
| name    | varchar(60) | NO   |     | NULL    |       |
| address | varchar(60) | NO   |     | NULL    |       |
| city    | varchar(60) | NO   |     | NULL    |       |
| state   | varchar(60) | NO   |     | NULL    |       |
| zip     | int(11)     | NO   |     | NULL    |       |

<br />

### Select a coloumn

Select the information or data that you want. `city` is a table name and `customers` is a table name.

```
SELECT city FROM customers
```

| <-T->                           | city      |
| :------------------------------ | :-------- |
| Edit, Inline Edit, Copy, Delete | City Name |
| Edit, Inline Edit, Copy, Delete | City Name |
| Edit, Inline Edit, Copy, Delete | City Name |
| Edit, Inline Edit, Copy, Delete | City Name |

<br />

### Run multiline command in sql

To run multi line command in SQL, use the semi column at the end of the line. Semi columns are not required in a single line command.

```
SELECT city FROM customers;
SELECT id FROM customers;
```

<br />

### Whitespace and new-line

Whitespace and new-line allowed in SQL for readability purpose.

```
SELECT       city
FROM customers
```

<br />

### Get multiple columns from a database

separates comma's through table name

```
SELECT name, zip FROM customers
```

| <-T->                           | city      | zip      |
| :------------------------------ | :-------- | :------- |
| Edit, Inline Edit, Copy, Delete | city name | zip Code |
| Edit, Inline Edit, Copy, Delete | city name | zip Code |
| Edit, Inline Edit, Copy, Delete | city name | zip Code |
| Edit, Inline Edit, Copy, Delete | city name | zip Code |

<br />

### Get all column from a database

Use asterisk symbol (\*) to retrieve all columns. This is a wild card statement.

```
SELECT * FROM customers
```

| <-T->                           | id     | name | zip      | address | city |
| :------------------------------ | :----- | :--- | :------- | :------ | :--- |
| Edit, Inline Edit, Copy, Delete | id no. | name | zip Code | address | city |
| Edit, Inline Edit, Copy, Delete | id no. | name | zip Code | address | city |
| Edit, Inline Edit, Copy, Delete | id no. | name | zip Code | address | city |
| Edit, Inline Edit, Copy, Delete | id no. | name | zip Code | address | city |

<br />

### Retrieve data from a column to a specific length

It will retrieve data from the beginning.

```
SELECT id, name FROM customers LIMIT 5
```

| <-T->                           | id  | name |
| :------------------------------ | :-- | :--- |
| Edit, Inline Edit, Copy, Delete | 1   | name |
| Edit, Inline Edit, Copy, Delete | 2   | name |
| Edit, Inline Edit, Copy, Delete | 3   | name |
| Edit, Inline Edit, Copy, Delete | 4   | name |
| Edit, Inline Edit, Copy, Delete | 5   | name |

<br />

### Retrieve data from a column to a specific length

Out of the two numbers given after the limit keyword, the first number is the starting point and second number is how many rows are retrieves.

```
SELECT id, name FROM customers LIMIT 5, 10
```

| <-T->                           | id  | name |
| :------------------------------ | :-- | :--- |
| Edit, Inline Edit, Copy, Delete | 6   | name |
| Edit, Inline Edit, Copy, Delete | 7   | name |
| Edit, Inline Edit, Copy, Delete | 8   | name |
| Edit, Inline Edit, Copy, Delete | 9   | name |
| Edit, Inline Edit, Copy, Delete | 10  | name |
| Edit, Inline Edit, Copy, Delete | 11  | name |
| Edit, Inline Edit, Copy, Delete | 12  | name |
| Edit, Inline Edit, Copy, Delete | 13  | name |
| Edit, Inline Edit, Copy, Delete | 14  | name |
| Edit, Inline Edit, Copy, Delete | 15  | name |

<br />

### SQL qualified names

fully qualified name. it has three parts separated by periods.

```
SELECT customers.name FROM customers
```

or

```
SELECT customers.name FROM youtube.customers
```

both are same as

```
SELECT name FROM customers
```

<br />

### Sorting single column
sorted alphabetically.
```
SELECT name FROM customers ORDER BY name
```

<br />

### Sorting single column with two column
sorted alphabetically.
```
SELECT name, city FROM customers ORDER BY id
```

<br />

### Sorting multiple column
This statement one order criteria first order by state and than by name.
```
SELECT state, city, name FROM customers ORDER BY state, name
```

| <-T->                           | statue | city        | name             |
| :------------------------------ | :--    | :---        |:--               |
| Edit, Inline Edit, Copy, Delete | AK     | Simmersville| Corey Smith      |
| Edit, Inline Edit, Copy, Delete | AK     | Anchorage   | Ruth Bolen       |
| Edit, Inline Edit, Copy, Delete | AL     | Tuscaloosa  | Crystal Jarvis   |
| Edit, Inline Edit, Copy, Delete | AL     | Montgomery  | Perry Jordan     |
| Edit, Inline Edit, Copy, Delete | AL     | Mobile      | Thomas Jackson   |
| Edit, Inline Edit, Copy, Delete | AR     | Texarkana   | Katherine Cain   |
| Edit, Inline Edit, Copy, Delete | AZ     | Mesa        | Debra Talkington |
| Edit, Inline Edit, Copy, Delete | AZ     | Phoenix     | Sherry Gibbons   |

<br />