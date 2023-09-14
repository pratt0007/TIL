# DBMS
## What is Data?
- Data is a collection of a distinct small unit of information. It can be used in a variety of forms like text, numbers, media, bytes, etc. it can be stored in pieces of paper or electronic memory, etc

## What is Database?

- A database is an organized collection of data, so that it can be easily accessed and managed.

- You can organize data into tables, rows, columns, and index it to make it easier to find relevant information.

- Database handlers create a database in such a way that only one set of software program provides access of data to all the users.

- The main purpose of the database is to operate a large amount of information by storing, retrieving, and managing data

### Data Integrity
- Data integrity refers to the overall accuracy, completeness, and reliability of data.
 #### 1. Domain Integrity-
 - restrict the format , type and volume of data stored by putting constraits or defining data type
#### 2. Entity Integrity :-
- The purpose is to ensure that data is not recorded multiple times. Eg making primary key
#### 3. Referncial Integrity
- Remove duplicate data record (Foreign Key concept)
#### 4. User Defined Integrity :-
- User constraints

## Types of Databases
- RDBMS - SQL
- File-Based
- Hierarchical Data Model
- Network data model
- Cloud database
- NoSQL Database
- The Object-Oriented Databases
- Graph Databases

### NoSQL DB
- A NoSQL database is an approach to design such databases that can accommodate a wide variety of data models. NoSQL stands for "not only SQL." It is an alternative to traditional relational databases in which data is placed in tables, and data schema is perfectly designed before the database is built.

- NoSQL databases are useful for a large set of distributed data.

- Some examples of NoSQL database system with their category are:

- MongoDB, CouchDB, Cloudant (Document-based)
- Memcached, Redis, Coherence (key-value store)
- HBase, Big Table, Accumulo (Tabular)

## Attributes  
- Single col in a table of database is called attribte
- Types - Simple
- Composite
- Multi-Valued
- Derived
### Defination
- A table in a db is called a relation.
- Properties of a Relation:
- Each relation has a unique name by which it is identified in the database.
- Relation does not contain duplicate tuples.
- The tuples of a relation have no specific order.
- All attributes in a relation are atomic, i.e., each cell of a relation contains exactly one value.
- ATTRIBUTES - COL
- TUPLE/RECORD - ROWS
- Degree The total number of attributes that comprise a relation is known as the degree of the table.
- Cardinality The total number of tuples at any one time in a relation is known as the table's cardinality. The relation whose cardinality is 0 is called an empty table.

## SQL Commands
DDL( Data definition Language)
- Structure of Database DRCAT (DROP)(CREATE)(ALTER)(TRUNCATE)
DML (Data Manipulation Lang)
- Manipulating data - DNU (DELETE)(INSERT)(UPDATE)
DCL (Data Control Language)
- Grant Revoke
TCL (Transcation Control language)
- Roll Back Save Point
DQL (Data Querry lang) 

  
## DBMS Architecture 
- The DBMS design depends upon its architecture. The basic client/server architecture is used to deal with a large number of PCs, web servers, database servers and other components that are connected with networks.
- The client/server architecture consists of many PCs and a workstation which are connected via the network.
- DBMS architecture depends upon how users are connected to the database to get their request done.

### Types of DBMS Architecture
1st Tier Architecture
- In this architecture, the database is directly available to the user. It means the user can directly sit on the DBMS and uses it.
- Any changes done here will directly be done on the database itself. It doesn't provide a handy tool for end users.
- The 1-Tier architecture is used for development of the local application, where programmers can directly communicate with the database for the quick response.

2nd Tier
- The 2-Tier architecture is same as basic client-server. In the two-tier architecture, applications on the client end can directly communicate with the database at the server side. For this interaction, API's like: ODBC, JDBC are used.
- The user interfaces and application programs are run on the client-side.
- The server side is responsible to provide the functionalities like: query processing and transaction management.
- To communicate with the DBMS, client-side application establishes a connection with the server side.

![image](https://github.com/pratt0007/TIL/assets/100209212/f696f046-b353-4332-9ff9-e558e583be7d)

3rd Tier
- The 3-Tier architecture contains another layer between the client and server. In this architecture, client can't directly communicate with the server.
- The application on the client-end interacts with an application server which further communicates with the database system.
- End user has no idea about the existence of the database beyond the application server. The database also has no idea about any other user beyond the application.
- The 3-Tier architecture is used in case of large web application.
![image](https://github.com/pratt0007/TIL/assets/100209212/abc4cc19-28de-4577-936c-6680fa4bf8fc)

# ACID Properties in DBMS
DBMS is the management of data that should remain integrated when any changes are done in it. It is because if the integrity of the data is affected, whole data will get disturbed and corrupted. Therefore, to maintain the integrity of the data, there are four properties described in the database management system, which are known as the ACID properties. The ACID properties are meant for the transaction that goes through a different group of tasks, and there we come to see the role of the ACID properties.

![image](https://github.com/pratt0007/TIL/assets/100209212/dc0f10c3-1a9d-4992-b661-ca34f1d2b651)
### 1) Atomicity
The term atomicity defines that the data remains atomic. It means if any operation is performed on the data, either it should be performed or executed completely or should not be executed at all. It further means that the operation should not break in between or execute partially. In the case of executing operations on the transaction, the operation should be completely executed and not partially executed.
### 2) Consistency
The word consistency means that the value should remain preserved always. In DBMS, the integrity of the data should be maintained, which means if a change in the database is made, it should remain preserved always. In the case of transactions, the integrity of the data is very essential so that the database remains consistent before and after the transaction. The data should always be correct.
### 3) Isolation
The term 'isolation' means separation. In DBMS, Isolation is the property of a database where no data should affect the other one and may occur concurrently. In short, the operation on one database should begin when the operation on the first database gets complete. It means if two operations are being performed on two different databases, they may not affect the value of one another. In the case of transactions, when two or more transactions occur simultaneously, the consistency should remain maintained. Any changes that occur in any particular transaction will not be seen by other transactions until the change is not committed in the memory.
### 4) 4) Durability
Durability ensures the permanency of something. In DBMS, the term durability ensures that the data after the successful execution of the operation becomes permanent in the database. The durability of the data should be so perfect that even if the system fails or leads to a crash, the database still survives. However, if gets lost, it becomes the responsibility of the recovery manager for ensuring the durability of the database. For committing the values, the COMMIT command must be used every time we make changes.



  

  
