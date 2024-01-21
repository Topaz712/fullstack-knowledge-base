# Introduction to Databases

## What are databases?

- We use databases to store data in a structured way on computer systems, making it easy to manage and access 

- They are crucial in various applications, especially for large multiuser setups where coordination is essential 

- Even individual users benefit from databases, like in electronic mail programs and personal organizers

# Databse Management Systems

- A Database Management System (DBMS) is software that organizes and stores data using standardized methods 

- With DBMS, tt allows data manipulation, since we can add, update, delete, or navigate/traverse data using standardized algorithms and queries

- We categorize DBMS based on data structures or types, it adapts smoothly to changes in our information systems as our organization's needs evolve
  - Adding new data categories doesn't disrupt the existing system

- This is crucial for effective data management and analysis 
  - For instance, creating a sales report for a salesteam detailing customers contacted and total sales in the last month would be challenging without a DBMS due to scattered data but a DBMS simplifies generating this with a few queries


- Various Database Management Systems exist, such as 
  - SQLite
  - MySQL
  - PostgreSQL
  - Microsoft Access
  - SQL Server
  - FileMaker
  - Oracle
  - RDBMS
  - dBASE
  - Clipper
  - FoxPro
  
Each has its advantages, disadvantages, and specific uses. 

## Types of Databases

We will deal with various database types but two major categories being:

- Relational `"SQL"` database
  - Stores data in tables

- Non-relational `"NoSQL"` databases store data
  - Using documents
  - Key-value pairs
  - Graph databases
  - or Wide-column stores
  
The main difference lies in how data is structured within these databases

## Knowing when to use relational vs non-relational databases

- We decide between relational and non-relational databases based on our data needs

- Relational databases like `MySQL` and `Oracle` store structured data in tables using SQL for defining and manipulating data 
  - *They're easy to extend and widely used in projects like WordPress/Drupal/Joomla* 
  
- Non-relational databases like `MongoDB/Cassandra/Neo4j` and `Redis` are for unstructured data 
  - *Using data models like document/graph/columnar and key-value; They're ideal for large databases with changing structures, seen in projects like Netflix/Twitter/LinkedIn*

Choosing between them depends on factors like data type, volume, performance, and team expertise

- Relational databases are best for  applications needing multi-row transactions like banking applications
- Non-relational databases are great for handling large data with evolving structures like video streaming applications

*We can even use both types in a single application, like using a relational database for user data and a non-relational one for user comments*

## Different types of SQL databases

We have various SQL databases, but the most common ones are MySQL, PostgreSQL, and SQLite

- MySQL 
  - It's the top open-source database, especially for platforms like WordPress/Drupal 
  - Known for its speedy reading operations, so it's excellent for applications that do a lot of reading

- PostgreSQL
  - Another open-source choice favored by big names like Apple, and what sets it apart is its reliability and data integrity 
  - It's great for tasks that involve a lot of writing and complex queries, perfect for analytics and data warehousing

- SQLite
  - A lightweight database used by applications like Firefox
  - Known for simplicity, it's simple and doesn't come with the complexities of a client-server database engine, making it a good fit for lightweight applications