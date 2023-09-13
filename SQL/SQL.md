# DATABASE (DB)
- A database is an organized collection of data, so that it can be easily accessed and managed.- 
- You can organize data into tables, rows, columns, and index it to make it easier to find relevant information
## Database Management Systems (DBMS)
- A special software program that helps users create and maintain a database
  - Makes it easy to manage large amounts of information
  - Handles Security & Backups
  - Importing/exporting data
  - Concurrency
  - Interacts with software applications
  - Programming Languages
### Relational Databases (SQL)
- Organize data into one or more tables
  - Each table has columns and rows
  - A unique key identifies each row
    - Row contains the information about a single object
    - Column conatins inforamtion about a single attribute
### Non Relatonal DataBase
- Organize data is anything but a traditional table
- Stores in document format like JSON , XML , BLOB files.
- Graphs
- Flexible Table
- EG- MongoDB , dynamoDB , Apache Cassandra , firebase etc.
#### JSON FILES
-   JSON stands for "JavaScript Object Notation." It is a lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate. JSON files are used for storing and exchanging data between a server and a client, or between different parts of an application.

#### XML FILES
- 
XML stands for "eXtensible Markup Language." XML is a markup language that was designed to store and transport data in a format that is both human-readable and machine-readable. It is a versatile and widely used format for representing structured data, making it useful in various domains and applications.


#### Database Queries
- Queries are requests made to the database management system for specific information

### Types of Keys:
#### Super Key:
- A super key is a group of single or multiple keys which identifies rows in a table.
#### Primary Key:
- A primary key, also called a primary keyword, is a column in a relational database table that's distinctive for each record.
#### Candidate Key:
- It is a set of attributes that uniquely identify tuples in a table. Candidate Key is a super key with no repeated attributes.
#### Alternate Key:
- It is a column or group of columns in a table that uniquely identify every row in that table.
```
  CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    employee_code VARCHAR(10) UNIQUE, -- This is an alternate key
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100) UNIQUE,
    hire_date DATE
);
```

#### Foreign Key:
- It is a column that creates a relationship between two tables. The purpose of Foreign keys is to maintain data integrity and allow navigation between two different instances of an entity.
```
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    total_amount DECIMAL(10, 2),
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```
#### Compound Key: 
- It has two or more attributes that allow you to uniquely recognize a specific record. It is possible that each column may not be unique by itself within the database.
```
CREATE TABLE orders (
    order_id INT,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10, 2),
    PRIMARY KEY (order_id, customer_id) // This is how we make 2 col primary 
);
```
#### Composite Key: 
- It is a combination of two or more columns that uniquely identify rows in a table. The combination of columns guarantees uniqueness, though individual uniqueness is not guaranteed.

#### Surrogate Key:
- An artificial key which aims to uniquely identify each record is called a surrogate key. These kind of key are unique because they are created when you don't have any natural primary key.

### Structured Query Language [(SQL)](https://www.w3schools.com/sql/default.asp):
- SQL is actually a hybrid language, it's basically 4 types of languages in one
  -  **Data Query Language (DQL)**
     -  Used to query the database for information.
     -  Get information that is already stored there
  - **Data Definition Language (DDL)**
    - Used for defining database schemas.
  - **Data Control Language (DCL)**
    - Used for controlling access to the data in the database.
    - User & permissions management
  - **Data Manipulation Language (DML)**
    - Used for inserting, updating and deleting data from the data
   
## Tables:
### SQL CREATE TABLE Statement:
- The `CREATE TABLE` statement is used to create a new table in a database.
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
- Creating a Table using another table.
```sql
CREATE TABLE new_table_name AS
    SELECT column1, column2,...
    FROM existing_table_name
    WHERE ....;
```
```
SELECT * INTO New_table_name FROM old_table_name;
```
### SQL DROP TABLE Statement:
- The `DROP TABLE` statement is used to drop an existing table in a database.
```sql
DROP TABLE table_name;
```
- To delete Data inside table:
  - The `TRUNCATE TABLE` statement is used to delete all the data inside a table, but not the table itself.
```sql
TRUNCATE TABLE table_name;
```
####  Difference between DELETE and TRUNCATE statements
```

There is a slight difference b/w delete and truncate statement. The DELETE statement only deletes the rows from the table based on the condition defined by WHERE clause or delete all the rows from the table when condition is not specified.

But it does not free the space containing by the table.

The TRUNCATE statement: it is used to delete all the rows from the table and free the containing space.
```
### ALTER TABLE Statement
- The `ALTER TABLE` statement is used to add, delete, or modify columns in an existing table. It can also be used to add and drop various constraints on an existing table.
```sql
-- Add Column
ALTER TABLE table_name
ADD column_name datatype;

-- Drop Column
ALTER TABLE table_name
DROP COLUMN column_name;

-- Rename Column
ALTER TABLE table_name
RENAME COLUMN old_name to new_name;

-- Modify Datatype
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```
### TEMP TABLES
- Temporary tables can be created at run-time and can do all kinds of operations that a normal table can do. These temporary tables are created inside tempdb database.
- There are two types of temp tables based on the behavior and scope.
-  1. Local Temp Variable
-  2. Global Temp Variable
#### LOCAL
```Local temp tables are only available at current connection time. It is automatically deleted when user disconnects from instances. It is started with hash (#) sign.

CREATE TABLE #local temp table (  
User id int,  
Username varchar (50),  
User address varchar (150)  
)
```
#### GLOBAL
```
Global Temp Variable
Global temp tables name starts with double hash (##). Once this table is created, it is like a permanent table. It is always ready for all users and not deleted until the total connection is withdrawn.

CREATE TABLE ##new global temp table (  
User id int,  
User name varchar (50),  
User address varchar (150)  
)  
```
### Constraints:
- Constraints can be specified when the table is created with the `CREATE TABLE` statement, or after the table is created with the `ALTER TABLE` statement.
```sql
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ....
);
```
#### NOT NULL Constraint:
- The `NOT NULL` constraint enforces a column to NOT accept NULL values.
#### UNIQUE Constraint:
- The `UNIQUE` constraint ensures that all values in a column are different. Both the `UNIQUE` and `PRIMARY KEY` constraints provide a guarantee for uniqueness for a column or set of columns.
- A `PRIMARY KEY` constraint automatically has a `UNIQUE` constraint. However, you can have many `UNIQUE` constraints per table, but only one `PRIMARY KEY` constraint per table.
#### DEFAULT Constraint:
- The `DEFAULT` constraint is used to set a default value for a column and will be passed as a value if no input is provided.

#### AUTO INCREMENT Field:
- Auto-increment allows a unique number to be generated automatically when a new record is inserted into a table. Not exactly a constraint but is passed into the table and this is normally used for a primary key.

### UPDATE Statement:
- The `UPDATE` statement is used to modify the existing records in a table.
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

-- If we omit WHERE -> all the values are updated.

UPDATE students  
SET User_Name = 'beinghuman'  
WHERE Student_Id = '3'  
```
### DELETE Statement:
- The `DELETE` statement is used to delete existing records in a table.
```sql
DELETE FROM table_name WHERE condition;
-- If we Omit WHERE -> all values are deleted


DELETE FROM EMPLOYEE WHERE ID=101;  
```

## SQL SELECT Statement:
- The `SELECT` statement is used to select data from a database. The data returned is stored in a result table, called the result-set.
- SQL SELECT DISTINCT: Retrieve unique values from a column or set of columns in a table.
- SQL SELECT COUNT: Calculate the number of rows in a table, optionally based on a specified condition.
- SQL SELECT LIMIT: Retrieve a specified number of rows from the beginning of a result set.
- SQL SELECT OFFSET and LIMIT: Retrieve a specified number of rows starting from a given position in a result set (used for pagination).
- SQL SELECT RANDOM: Retrieve random rows from a table.
- SQL SELECT IN: Retrieve rows where a specified column matches any value in a list.
- SQL SELECT Multiple Columns: Retrieve specific columns from a table.
- SQL SELECT DATE: Retrieve rows based on date-related conditions.
- SQL SELECT SUM: Calculate the sum of values in a column, optionally based on a condition.
- SQL SELECT NULL: Retrieve rows where a specified column has a NULL value.

```
SELECT DISTINCT column1, column2, ...
FROM table_name;

SELECT COUNT(*) 
FROM table_name;

SELECT COUNT(*) 
FROM table_name 
WHERE condition;

SELECT column1, column2, ...
FROM table_name
LIMIT number_of_rows OFFSET offset_value;

SELECT column1, column2, ...
FROM table_name
ORDER BY RAND()
LIMIT number_of_rows;

SELECT column1, column2, ...
FROM table_name
WHERE column_name IN (value1, value2, ...);
```
```sql
-- Select certain columns from the table
SELECT column1, column2, ...
FROM table_name;

-- Select the whole table
SELECT * FROM table_name;
```
### ORDER BY Keyword:
- The `ORDER BY` keyword is used to sort the result-set in ascending or descending order.
- If we don't specify the order it needs to be returned in, it defualts to acending order.
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;

-- Also we could be selective in ordering the table:
-- In this, we first order according to columnx, if there is a clash then we order those objects according to columny
SELECT *
FROM table_name
ORDER BY columnx, columny;
```

### WHERE Clause:
- The `WHERE` clause is used to filter records. It is used to extract only those records that fulfil a specified condition.
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;

-- Operators which can be used in the WHERE Statements
=            Equal
>            Greater than
<            Less than
>=           Greater than or equal
<=           Less than or equal
<>           Not equal

BETWEEN      Between a certain range
  WHERE column_name BETWEEN value1 AND value2;
LIKE         Search for a pattern
  WHERE column_name LIKE pattern;
IN           To specify multiple possible values for a column
  WHERE column_name IN (value1, value2, ...);
```

### AS clause:
- The `AS` command is used to rename a column or table with an alias.
```sql
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers;
```

### SELECT DISTINCT Statement:
- The `SELECT DISTINCT` statement is used to return only distinct (different) values.
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

### GROUP BY Statement:
- The `GROUP BY` statement groups rows that have the same values into summary rows, like "find the number of customers in each country".
- The `GROUP BY` statement is often used with aggregate functions (`COUNT()`, `MAX()`, `MIN()`, `SUM()`, `AVG()`) to group the result-set by one or more columns.
```sql
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

