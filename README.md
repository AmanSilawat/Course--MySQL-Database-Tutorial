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

```sql
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

```sql
SHOW TABLES
```

| Tables_in_youtube |
| :---------------- |
| customers         |

<br />

### Show all headings from a database

Table name must be in lowercase. When ever do you run this command then return the names of columns i.e. `id`, `name`, etc and some other information. `PRI` mean this a primary key.

```sql
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

```sql
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

```sql
SELECT city FROM customers;
SELECT id FROM customers;
```

<br />

### Whitespace and new-line

Whitespace and new-line allowed in SQL for readability purpose.

```sql
SELECT       city
FROM customers
```

<br />

### Get multiple columns from a database

separates comma's through table name

```sql
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

```sql
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

```sql
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

```sql
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

```sql
SELECT customers.name FROM customers
```

or

```sql
SELECT customers.name FROM youtube.customers
```

both are same as

```sql
SELECT name FROM customers
```

<br />

### Sorting single column

sorted alphabetically. The default sort will be in **ascending** order.

```sql
SELECT name FROM customers ORDER BY name
```

<br />

### Sorting single column with two column

sorted alphabetically.

```sql
SELECT name, city FROM customers ORDER BY id
```

<br />

### Sorting multiple column

This statement one order criteria first order by state and than by name.

```sql
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

```sql
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

```sql
SELECT name, id FROM customers ORDER BY id DESC LIMIT 1
```

| id  | name         |
| :-- | :----------- |
| 96  | Lucy Bronson |

<br />

### Get specific row

```sql
SELECT id, name FROM customers WHERE id=56
```

| id  | name           |
| :-- | :------------- |
| 56  | Sherry Gibbons |

<br />

### Get rows but specific row not contain

```sql
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

```sql
SELECT id, name FROM customers WHERE id < 4
```

| id  | name          |
| :-- | :------------ |
| 1   | Bucky Roberts |
| 2   | Noah Parker   |
| 3   | Kelsey Burger |

<br />

### Get rows less than and equal to specific number

```sql
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

```sql
SELECT id, name FROM customers WHERE id > 4
```

<br />

### Get rows grater than equal to specific number

```sql
SELECT id, name FROM customers WHERE id >= 4
```

<br />

### Get rows between two numbers

```sql
SELECT id, name FROM customers WHERE id BETWEEN 25 AND 30
```

<br />

### Get rows between filtering with string

```sql
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

### Advanced Filtering Using AND

```sql
SELECT name, state, city FROM customers WHERE state='CA' AND city = 'Hollywood'
```

| name           | state | city      |
| :------------- | :---- | :-------- |
| Jack Nicholson | CA    | Hollywood |

<br />

### Advanced Filtering Using OR

```sql
SELECT id, city FROM customers WHERE city='Denver' OR city='Provo'
```

| id  | city   |
| :-- | :----- |
| 16  | Denver |
| 17  | Provo  |
| 60  | Provo  |

### Advanced Filtering Using AND and OR <span style="color:red">: Wrong Way</span>

`id=1` or `id=2` is true but city portion is not correct.
This query mean:

-   `id=1` must be in `city=Raleigh` but `id=2` should be in `city=Raleigh`
-   Aame as
-   `id=2` must be in `city=Raleigh` but `id=1` should be in `city=Raleigh`

```sql
SELECT id, name, city FROM customers WHERE id=1 or id=2 AND city = 'Raleigh'
```

| id  | name          | city                                       |
| :-- | :------------ | :----------------------------------------- |
| 1   | Bucky Roberts | <span style="color:red">Noah Parker</span> |
| 2   | Adams         | Raleigh                                    |

<br />

### Advanced Filtering Using AND and OR <span style="color:green">: Correct Way</span>

You use multiple **AND** and **OR** statement make sure that you use parentheses because

```sql
SELECT id, name, city FROM customers WHERE id=1 or (id=2 AND city = 'Raleigh')
```

| id  | name          | city                                         |
| :-- | :------------ | :------------------------------------------- |
| 1   | Bucky Roberts | <span style="color:green">Noah Parker</span> |
| 2   | Adams         | Raleigh                                      |

<br />

### Filtering Using AND and OR with another way <span style="color:green">: Correct Way</span>

Get the row of whatever id matches

```sql
SELECT id, name, city FROM customers WHERE (id=1 or id=2) AND city = 'Raleigh'
```

| id  | name  | city    |
| :-- | :---- | :------ |
| 2   | Adams | Raleigh |

<br />

### IN statement

### Multiple or statement: Not use this

Because this is a long way instead use `IN` statement.

```sql
SELECT name, state FROM customers WHERE state='CA' OR state='NC' OR state='NY'
```

| name           | state |
| :------------- | :---- |
| Bucky Roberts  | NY    |
| Noah Parker    | NC    |
| Kelsey Burger  | CA    |
| Jack Nicholson | CA    |
| Devon Myers    | NY    |
| Harry Brown    | NC    |

<br />

#### Not contains in state column

```sql
SELECT name, state FROM customers WHERE state NOT IN ('CA', 'NC', 'NY')
```

| name            | state |
| :-------------- | :---- |
| Corey Smith     | AK    |
| Harry Potter    | NJ    |
| Henry Jackson   | IN    |
| Cynthia Alvarez | GA    |
| Teresa Smith    | PA    |
| Gary Foster     | IN    |

<br />

### Filtering wild card
#### Start with begin (%)
All name start with `new`

```sql
SELECT name FROM items WHERE name LIKE 'new%'
```

| name                          |
| :--------------               |
| New gym socks                 |
| New ipad stolen from best buy |
| new curtain for bedroom       |
| newspaper                     |

<br />

#### Start with end (%)
All name start with `new`
```sql
SELECT name FROM items WHERE name LIKE 'new%'
```

| name                 |
| :--------------      |
|3 boxes of frogs      |
|48 boxes of frogs     |
|7 boxes of frogs      |

<br />

#### Word contains in between (%)
```sql
SELECT name FROM items WHERE name LIKE '%computer%'
```

| name                          |
| :--------------               |
| Brand New iMac Computer       |
| awesome alien computer game   |
| supercomputer                 |
| computer                      |

<br />

#### start and and with a specific word (%)

```sql
SELECT city FROM customers WHERE city LIKE 'h%d'
```

| city       |
| :--------- |
| Hollywood  |
| Highland   |

<br />

####  only one character wild card (_)
`_` mean only one character find but use `%` symbol to select multiple characters.

```sql
SELECT name FROM items WHERE name LIKE '_ boxes of frogs'
```

| city              |
| :---------        |
| 3 boxes of frogs  |
| 7 boxes of frogs  |

<br />

### Regex Search
#### Search a word

```sql
SELECT name FROM items WHERE name REGEXP 'new'
```

| name                           |
| :--                            |
| Brand New iMac Computer        |
| New gym socks                  |
| New ipad stolen from best buy  |
| new curtain for bedroom        |
| newspaper                      |

<br />

#### End with specific word

```sql
SELECT name FROM items WHERE name REGEXP '.boxes'
```
| name             |
| :--              |
|3 boxes of frogs  |
|48 boxes of frogs |
|7 boxes of frogs  |

<br />

#### OR statement in REGEXP

```sql
SELECT name FROM items WHERE name REGEXP 'gold|car'
```
| name               |
| :--                |
| traditional carpet |
| gold necklace      |
| used car           |
| gold earring       |
| scarf              |

<br />

#### Find specific numbers

```sql
SELECT name FROM items WHERE name REGEXP '[12345] boxes of frogs'
```
Same as
```sql
SELECT name FROM items WHERE name REGEXP '[1-5] boxes of frogs'
```

| name               |
| :--                |
| 3 boxes of frogs   |

<br />

#### Negate Numbers

```sql
SELECT name FROM items WHERE name REGEXP '[^12345] boxes of frogs'
```

| name               |
| :--                |
| 48 boxes of frogs  |
| 7 boxes of frogs   |

<br />

### Creating Custom Columns
#### Join to column

```sql
SELECT CONCAT(city, ', ', state) FROM customers
```

| CONCATE(city, ', ', state)|
| :--                       |
|Adams, NY                  |
|Raleigh, NC                |
|Oakland, CA                |
|Simmersville, AK           |
|Newark, NJ                 |
|Gary, IN                   |
|Augusta, GA                |

<br />

#### Join column and set a column name

```sql
SELECT CONCAT(city, ', ', state) AS new_address FROM customers
```
| new_address      |
| :--              |
|Adams, NY         |
|Raleigh, NC       |
|Oakland, CA       |
|Simmersville, AK  |
|Newark, NJ        |
|Gary, IN          |
|Augusta, GA       |

<br />

#### perform mathematical calculation on column
You can do all kinds of calculations. like `cost-1`, `cost+1`, `cost*1`, `cost/1`, `cost%1` and etc.

```sql
SELECT name, cost, cost-1 FROM items
```

| name                          | cost     | cost-1            |
| :--                           | :--      | :--               |  
| Brand New iMac Computer       | 149.99   |148.99000549316406 |
| used diaper from my sister    | 2.04     |1.0399999618530273 |
| Fresh apple pie               | 14.99    |13.989999771118164 |

<br />

#### set a column name with mathematical calculation

```sql
SELECT name, cost, cost-1 AS sale_price FROM items
```
| name                          | cost     | sale_price        |
| :--                           | :--      | :--               |  
| Brand New iMac Computer       | 149.99   |148.99000549316406 |
| used diaper from my sister    | 2.04     |1.0399999618530273 |
| Fresh apple pie               | 14.99    |13.989999771118164 |

<br />

### Functions

#### UPPER

```sql
SELECT name, UPPER(name) AS name_upp, city, UPPER(city) as city_upper FROM customers
```


|name          | name_upp       | city      | city_upper |
|:--           |:--             |:--        |:--         |
|Bucky Roberts | BUCKY ROBERTS  | Adams     | ADAMS      |
|Noah Parker   | NOAH PARKER    | Raleigh   | RALEIGH    |
|Kelsey Burger | KELSEY BURGER  | Oakland   | OAKLAN     |

<br />

### Aggregate Functions
An aggregate function performs a calculation on a set of values, returns a single value. aggregate functions ignore null values.
#### SQRT

```sql
SELECT cost, SQRT(cost) AS square_root FROM items
```

| cost   | square_root        |
|:---    |:---                |
| 149.99 | 12.247040683086018 |
| 2.04   | 1.4282856723544584 |

<br />

#### SQRT

```sql
SELECT AVG(cost) AS average_cost FROM items
```

| average_cost       |
|:---                |
| 463.93710062742235 |

<br />

#### SUM

```sql
SELECT SUM(bids) AS total_bids FROM items
```

| total_bids |
|:---        |
| 10939      |

<br />

### Aggregate Functions more
#### count the same name with in a column

```sql
SELECT COUNT(name) FROM items WHERE seller_id=18
```

| COUNT(name) |
|:---         |
| 4           |

<br />

#### Calculate the average of a column

```sql
SELECT AVG(cost) FROM items WHERE seller_id=18
```

| AVG(cost)           |
|:---                 |
| 237.77499914169312  |

<br />

#### Use multiple aggregate function

```sql
SELECT COUNT(*) AS item_count,
Max(cost) AS max,
AVG(cost) AS avg
FROM items WHERE seller_id=1
```

|item_count |max | avg                 |
|:--        |:-- |:---                 |
|2          |2.5 | 2.2699999809265137  |

