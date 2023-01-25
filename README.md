# Lab 1

## Broad overview

A **database** may be defined as a structured set of data (more on what that might mean in later lessons).  

A **database management system (DBMS)** is the program(s) used to access and manipulate that data.  We will frequently abuse the term *database* and use it to refer to both the data **and** the program (which would, more properly, be called a DBMS)

Broadly speaking databases fall into two major categories:
  * SQL
  * NoSQL
  
SQL stands for **Structured Query Language**.  It is the language used to organize, add, remove, and modify the data in an SQL DBMS (big surprise right?).  It is also the language we will use to transform raw data into useable information.  A few well-known examples of SQL DBMS include MySQL, Oracle, SQL Server, and MariaDB.  In an SQL database information is stored as **tables**.  A table is a two-dimensional array of data.  The *rows* are known as **records**, and the columns are known as **fields**.

NoSQL is a broad term encompassing many types of databases that organize their data differently than SQL-style databases.  Some well known examples include mongoDB and Neo4J.  NoSQL databases give up consistency guarantees that an SQL DBMS can provide in exchange for improved scalability (which is why they are so popular for applications like Facebook).  There is much more variety in the way that a NoSQL database structures its data, but several are closely associated with structured data formats like XML or JSON.  

We are going to spend about two-thirds of our time with the SQL DBMS known as SQL Server.  SQL Server is an Enterprise level database from Microsoft.

We are going to focus on SQL Server because:

  * Enterprise Level, 
  * Actively developed, 
  * Student Development License,
  * Powerful.  

### Relational Databases

SQL databases are **relational Databases (RDBMS)**.  The data is organized around the idea of

* Databases
* Tables
* Records
* Fields

The data is an abstraction of the TABLE.  Most RDBMS use the SQL language to 

* extract data, 
* insert data, 
* update data and,
* create structures.

The entire organizational system is secretely based around the ideas of SETS or ordered elements which we will explore in greater detail later.

## SQL Server: a first pass

As you go through the exercises below, you may find the [references](#references) below useful.

### Log into Azure Data Studio

1. Start by logging into a Linux machine in either 2610 or 2650.
2. Run the program 'Azure Data Studio'.
3. Connect to the Server I give you and use the SQL Login credentials I give you the first day of class.

You are using the `Azure Data Studio` client.  

### Poke around a bit

Look at the databases in the system:
Open a New Query window 

Change to the database 'DBName':
--WHere DBName is the name of your database, First Initial of first name and last name so Peter Smith would be PSmith.

```
use DBName;
```

See what tables are in that database:

Look at the contents of Departments (SQL Server is NOT case sensitive when it comes to table names):

```
select * from Departments;
```

Get a sense for the structure of that database:


### Create a Schema

You will need to create a schema for Lab 1 (and a second schema we'll use in a bit called Lab01Tmp, everything else will be created from the database.

```
CREATE SCHEMA Lab01;  
GO
```

Sometimes it may be necessary to remove a Schema in that instance use the following

```
DROP SCHEMA <name>;
```
Drop your Lab01Tmp schema.

It is **very** common to use the keyword `DROP` to remove an object (a user, a database, a table, schema, etc).

Now that you have removed your Lab01Tmp (I'll be checking the schema list as part of your grade so make sure you remove the Tmp one).

## Exercises

I'm going to ask you to do a series of tasks that will probably require you to look a few things up
online. I've included some references for this lab (down below), but in the future you'll want to figure out
how to google (bing) your way to the exact format of a command and examples. In particular you are going to need to figure out how the `CREATE TABLE` and `INSERT` statements work.  You will also need to figure out a little bit about SQL data-types.  If you have any questions feel free to ask.  
With that in mind, here's what I
want you to do (or have already done):

1. Create your schema (this should already be completed).  You will use this schema for all your Lab 1 work.
1. Create a table called `test` (within your Lab01 schema) with ONE column named `test_field`<BR>the data-type of `test_field` must be TEXT and you should insert your last name into the table.
1. Create a table called `workers` (within your Lab01 schema) with the following fields (all capital):

Column Name | Description
------------|--------------
EMPLOYEE    | The person's name
MANAGER     | The manager's name
JOB         | A job title
SALARY      | a yearly salary
YEARS_WORKED| The number of years worked

You get to pick the data-types for the fields

1. Enter data that satisfies ALL of the following restrictions into your table:
  *  Roberts, Ruskin, and Raphael are all ticket agents.
  *  Rayburn is a baggage handler.
  *  Rice is a flight mechanic.
  *  Price manages all ticket agents.
  *  Powell manages Rayburn.
  *  Porter manages Rice, Price, Powell and himself.
  *  Powell is head of ground crews and Porter is chief of operations.
  *  Every employee receives a 10% raise for each complete year worked.
  *  Roberts, Ruskin, Raphael, and Rayburn all started at $12,000. Roberts just started work, Ruskin
and Raphael have worked for a year and a half, and Rayburn has worked for 2 years.
  *  Rice started at $18,000 and now makes $21,780.
  *  Price and Powell started at $16,000 and have both been working for three years.
  *  Porter started at $20,000 and has been around two years longer than anyone else.

## Checklist of things to do

* [ ] Play around a bit, logged in as `temp_admin` (see above).
* [ ] Submit your schema name as what you "turn in" for this lab.
* [ ] Do the Exercises above (the contents of your database will be used for grading).

## References

Use these references for review and to learn some new things that you'll be needing:

  * data types:
    [https://learn.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql?view=sql-server-ver16]
  * Nice intro to creating tables:
    [https://learn.microsoft.com/en-us/sql/relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables?view=sql-server-ver16]
  * Inserting data (contains more than you need right now):
    [https://learn.microsoft.com/en-us/sql/relational-databases/native-client-ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters?view=sql-server-ver16]
  * SQL Server Documentation
    [https://learn.microsoft.com/en-us/sql/sql-server/?view=sql-server-ver16]
