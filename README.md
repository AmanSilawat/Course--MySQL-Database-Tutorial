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

| city      |
| :-------- |
| City Name |
| City Name |
| City Name |
| City Name |

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

| city      | zip      |
| :-------- | :------- |
| city name | zip Code |
| city name | zip Code |
| city name | zip Code |
| city name | zip Code |

<br />

### Get all column from a database

Use asterisk symbol (\*) to retrieve all columns. This is a wild card statement.

```
SELECT * FROM customers
```

| id     | name | zip      | address | city |
| :----- | :--- | :------- | :------ | :--- |
| id no. | name | zip Code | address | city |
| id no. | name | zip Code | address | city |
| id no. | name | zip Code | address | city |
| id no. | name | zip Code | address | city |

<br />

### Retrieve data from a column to a specific length

It will retrieve data from the beginning.

```
SELECT id, name FROM customers LIMIT 5
```

| id  | name |
| :-- | :--- |
| 1   | name |
| 2   | name |
| 3   | name |
| 4   | name |
| 5   | name |

<br />

### Retrieve data from a column to a specific length

Out of the two numbers given after the limit keyword, the first number is the starting point and second number is how many rows are retrieves.

```
SELECT id, name FROM customers LIMIT 5, 10
```

| id  | name |
| :-- | :--- |
| 6   | name |
| 7   | name |
| 8   | name |
| 9   | name |
| 10  | name |
| 11  | name |
| 12  | name |
| 13  | name |
| 14  | name |
| 15  | name |

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

sorted alphabetically. The default sort will be in **ascending** order.

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

| statue | city         | name             |
| :----- | :----------- | :--------------- |
| AK     | Simmersville | Corey Smith      |
| AK     | Anchorage    | Ruth Bolen       |
| AL     | Tuscaloosa   | Crystal Jarvis   |
| AL     | Montgomery   | Perry Jordan     |
| AL     | Mobile       | Thomas Jackson   |
| AR     | Texarkana    | Katherine Cain   |
| AZ     | Mesa         | Debra Talkington |
| AZ     | Phoenix      | Sherry Gibbons   |

<br />

### Descending sorting single column

alphabetically Descending sorting.

```
SELECT name FROM customers ORDER BY name DESC
```

<br />

### Descending sorting single column with two column

alphabetically Descending sorting.

```
SELECT name, city FROM customers ORDER BY id DESC
```

<br />

### Retrieve the row whose ID is the highest.

```
SELECT name, id FROM customers ORDER BY id DESC LIMIT 1
```

| id  | name         |
| :-- | :----------- |
| 96  | Lucy Bronson |

<br />

### Get specific row

```
SELECT id, name FROM customers WHERE id=56
```

| id  | name           |
| :-- | :------------- |
| 56  | Sherry Gibbons |

<br />

### Get rows but specific row not contain

```
SELECT id, name FROM customers WHERE id != 56
```

| id  | name          |
| :-- | :------------ |
| 54  | David Turner  |
| 55  | Bucky Roberts |
| 57  | Noah Parker   |
| 58  | Kelsey Burger |

<br />

### Get rows less than specific number

```
SELECT id, name FROM customers WHERE id < 4
```

| id  | name          |
| :-- | :------------ |
| 1   | Bucky Roberts |
| 2   | Noah Parker   |
| 3   | Kelsey Burger |

<br />

### Get rows less than and equal to specific number

```
SELECT id, name FROM customers WHERE id <= 4
```

| id  | name          |
| :-- | :------------ |
| 1   | Bucky Roberts |
| 2   | Noah Parker   |
| 3   | Kelsey Burger |
| 4   | Corey Smith   |

<br />

### Get rows grater than specific number

```
SELECT id, name FROM customers WHERE id > 4
```

<br />

### Get rows grater than equal to specific number

```
SELECT id, name FROM customers WHERE id >= 4
```

<br />

### Get rows between two numbers

```
SELECT id, name FROM customers WHERE id BETWEEN 25 AND 30
```

<br />

### Get rows between filtering with string

```
SELECT id, state FROM customers WHERE state = 'CA'
```

| id  | state |
| :-- | :---- |
| 3   | CA    |
| 11  | CA    |
| 32  | CA    |
| 51  | CA    |
| 64  | CA    |
| 75  | CA    |

<br />
