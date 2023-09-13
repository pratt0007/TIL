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
#### Foreign Key:
- It is a column that creates a relationship between two tables. The purpose of Foreign keys is to maintain data integrity and allow navigation between two different instances of an entity.
#### Compound Key: 
- It has two or more attributes that allow you to uniquely recognize a specific record. It is possible that each column may not be unique by itself within the database.
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
