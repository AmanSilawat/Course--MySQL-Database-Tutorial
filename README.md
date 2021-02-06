# Course--MySQL-Database-Tutorial
Referenced link: [thenewboston - MySQL Database Tutorial](https://www.youtube.com/playlist?list=PL32BC9C878BA72085)

## Introduction to Databases
### What is a database?
Database is a collection of data. In which we can make "tables". table store some related information. 

#### table
- table are made of "column" and "rows".
- Column are like categories
- Each entry is on a separate row.

##### Primary Keys
- all tables should have "primary keys".
- no rows can have same primary key

##### Table demo
| ID | Name     | Age  |
|:-- |:------   |:-----|
| 1  | User 1   | 20   |
| 2  | User 2   | 22   |
| 3  | User 3   | 28   |

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

|Database          |
|:---------------  |
|information_schema|
|mysql             |
|performance_schema|
|phpmyadmin        |
|test              |
|youtube           |

<br />

### Show all tables from a database
Returns the table from a specific database.
```
SHOW TABLES
```
|Tables_in_youtube|
|:--------------- |
|customers        |

<br />

### Show all headings from a database
Table name must be in lowercase. When ever do you run this command then return the names of columns i.e. `id`, `name`, etc and some other information. `PRI` mean this a primary key.
```
SHOW COLUMNS FROM customers
```

| Field   | Type       | Null | Key  | Default   | Extra |
|:------- |:---------- |:---- |:---- |:--------- |:----- |
| id      | int(11)    | NO   | PRI  | NULL      |       |
| name    | varchar(60)| NO   |      | NULL      |       |
| address | varchar(60)| NO   |      | NULL      |       |
| city    | varchar(60)| NO   |      | NULL      |       |
| state   | varchar(60)| NO   |      | NULL      |       |
| zip     | int(11)    | NO   |      | NULL      |       |

<br />

### Select a coloumn
Select the information or data that you want. `city` is a table name and `customers` is a table name.
```
SELECT city FROM customers
```

|<-T->                          |city              |
|:----------------------------- |:---------------  |
|Edit, Inline Edit, Copy, Delete|City Name         |
|Edit, Inline Edit, Copy, Delete|City Name         |
|Edit, Inline Edit, Copy, Delete|City Name         |
|Edit, Inline Edit, Copy, Delete|City Name         |

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
|<-T->                          |city      |zip       |
|:----------------------------- |:-------- |:-------- |
|Edit, Inline Edit, Copy, Delete|city name |zip Code  |
|Edit, Inline Edit, Copy, Delete|city name |zip Code  |
|Edit, Inline Edit, Copy, Delete|city name |zip Code  |
|Edit, Inline Edit, Copy, Delete|city name |zip Code  |

<br />

###  Get all column from a database
Use asterisk symbol (*) to retrieve all columns. This is a wild card statement.
```
SELECT * FROM customers
```

|<-T->                          |id      |name    | zip       |address       |city       |
|:----------------------------- |:------ |:------ |:-------- |:-------- |:-------- |
|Edit, Inline Edit, Copy, Delete|id no.  |name    | zip Code  |address  |city  |
|Edit, Inline Edit, Copy, Delete|id no.  |name    | zip Code  |address  |city  |
|Edit, Inline Edit, Copy, Delete|id no.  |name    | zip Code  |address  |city  |
|Edit, Inline Edit, Copy, Delete|id no.  |name    | zip Code  |address  |city  |