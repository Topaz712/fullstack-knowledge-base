# Introduction to SQL

## What is SQL?

- `SQL "Structured Query Language"` is a programming language for communicating/interacting with data in a relational database management system
  - Its syntax resembles English, making it easy to write, read, and understand
  - We use SQL to retrieve, insert, update, and delete data in databases

- It's the standard language for storing, manipulating, and retrieving database data

*The choice of SQL database doesn't matter much, as the syntax is generally compatible across all databases*

## Creating Tables

```
CREATE TABLE Employees (
    EmployeeID int,
    LastName varchar(255),
    FirstName varchar(255),
    BirthDate date,
    Notes text
);

INSERT INTO Employees (EmployeeID, LastName, FirstName, BirthDate, Notes)
VALUES (1, 'Doe', 'John', '1990-01-01', 'John Doe was born on January 1, 1990.');
INSERT INTO Employees (EmployeeID, LastName, FirstName, BirthDate, Notes)
VALUES (2, 'Doe', 'Jane', '1991-02-02', 'Jane Doe was born on February 2, 1991.');
INSERT INTO Employees (EmployeeID, LastName, FirstName, BirthDate, Notes)
VALUES (3, 'Doe', 'Mary', '1992-03-03', 'Mary Doe was born on March 3, 1992.');
INSERT INTO Employees (EmployeeID, LastName, FirstName, BirthDate, Notes)
VALUES (4, 'Doe', 'Mark', '1993-04-04', 'Mark Doe was born on April 4, 1993.');
INSERT INTO Employees (EmployeeID, LastName, FirstName, BirthDate, Notes)
VALUES (5, 'Doe', 'Lisa', '1994-05-05', 'Lisa Doe was born on May 5, 1994.');
INSERT INTO Employees (EmployeeID, LastName, FirstName, BirthDate, Notes)
VALUES (6, 'Doe', 'Robert', '1995-06-06', 'Robert Doe was born on June 6, 1995.');

```
- In SQL, data is organized into tables, each having columns and rows 
- Tables categorize information, like Employees, Products, customers, orders, invoices and etc.. 
- Creating a table involves using the `CREATE TABLE` statement, specifying columns and their data types, so for example, we can create an "Employees" table with columns like EmployeeID, LastName, FirstName, BirthDate, and Notes

A little on understanding the data types used:

- int: For integer numbers
- varchar: For variable-length character strings
- date: For date values
- text: For long text strings

Other data types include:

- float: For floating-point numbers
- decimal: For decimal numbers
- boolean: For boolean values (true/false)
- blob: For binary data
- json: For storing JSON data
- uuid: For storing UUIDs
- array: For storing arrays

We have to consider the size of data for performance, like if a column stores values up to 255 characters, using `varchar(255)` is better than `text` 
Similarly, if it's up to 10 characters, `varchar(10)` is preferred, improving memory efficiency

Reviewing the columns in the **Employees** table:

- EmployeeID: An integer uniquely identifying each employee
- LastName: A variable-length character string storing the last name
- FirstName: A variable-length character string storing the first name
- BirthDate: A date value storing the birth date
- Notes: A long text string storing notes about the employee

For the code: 
```INSERT INTO Employees (EmployeeID, LastName, FirstName, BirthDate, Notes)
VALUES (1, 'Doe', 'John', '1990-01-01', 'John Doe was born on January 1, 1990.');
```
- `INSERT INTO`: This clause adds specified rows into the table
  - To insert data, we use the `INSERT INTO` statement 
- `Employees`: The table's name
- `(EmployeeID, LastName, FirstName, BirthDate, Notes)`: Parameters listing the columns for which values will be inserted by `INSERT INTO` statement
- `VALUES`: A clause indicating the data being inserted, aligned with the column order specified in `INSERT INTO`

*It's important to note how crucial this statement is for adding new data to the Employees table in a structured way*

## Selecting Data and Where Clause

- Selecting data involves using the `SELECT` statement, which retrieves rows from a table

```
SELECT * FROM Employees;
```
- `SELECT`: A clause indicating a query, used whenever we retrieve data from a database
- `*`: A wildcard character representing all columns, fetching every column from the Employees table
- `FROM` Employees: A clause specifying the table from which data is queried
- `;`: A semicolon indicating the end of the statement; although optional, it's a good practice to include

So this statement forms a query
  - Which is a request for data from a database table 
  - The result set, is like a temporary table, holds the data returned by the query, even if it's empty

or

```
SELECT FirstName, LastName FROM Employees;
```
- We can filter results using the `WHERE` clause to filter the result set to include on rows that meet specifying conditions like `FirstName = 'John'` 
  - This is crucial for focusing on specific data, improving efficiency, and reducing server load
ex. `SELECT * FROM Employees WHERE FirstName = 'John';`
will return: `1|Doe|John|1990-01-01|John Doe was born on January 1, 1990.`

So for codes:
1. `SELECT * FROM Employees WHERE FirstName = 'John' AND LastName = 'Doe';`
2. `SELECT * FROM Employees WHERE FirstName = 'John' OR LastName = 'Doe';`
3. `SELECT * FROM Employees WHERE NOT FirstName = 'John';`
returns:
1. `1|Doe|John|1990-01-01|John Doe was born on January 1, 1990.`
2. 
```
1|Doe|John|1990-01-01|John Doe was born on January 1, 1990.
2|Doe|Jane|1991-02-02|Jane Doe was born on February 2, 1991.
```
3. `2|Doe|Jane|1991-02-02|Jane Doe was born on February 2, 1991.`

This is because:
- `AND` Operator: Combines two conditions, ensuring both must be true for a row to be included in the result set
- `OR` Operator: Combines two conditions, including a row if either condition is true
- `NOT` Operator: Negates the condition, displaying records where the specified condition is **NOT TRUE**

### The importance of the `WHERE` Clause is based on:

- **Efficiency**: Extracts only needed data from a table, reducing server load and enhancing application performance
- **Bandwidth**: Aids in bandwidth management, crucial for tables with millions of rows
- **Security**: Supports row-level security, limiting user access to specific data 'a very powerful feature of SQL'
- *Cost Efficiency*: Reduces costs, especially in cloud databases, where charges may be based on data volume

## ORDER BY and LIMIT Clause

- Ordering results is achieved with the `ORDER BY` clause 
  - It sorts the result set in ascending order by default
  - Code: `SELECT * FROM Employees ORDER BY FirstName;`, sorts the result set by FirstName in ascending order 
  - Code: `SELECT * FROM Employees ORDER BY FirstName DESC;`, the DESC keyword sorts in descending order

- The `LIMIT` clause restricts the number of rows returned by a query 
  - Code: `SELECT * FROM Employees LIMIT 3;` retrieves the first 3 rows 
    - This reduces the amount of data needed and speeds up our application

- Additionally, the `OFFSET` clause, combined with `ORDER BY`, allows retrieving rows beyond the specified limit, like `SELECT * FROM Employees ORDER BY EmployeeID DESC LIMIT 3;` for the last 3 rows
  - This works because of the way a SQL query is executed from left to right
  - In this code it sorts the result set in descending order by the *EmployeeID* column and selects the first 3 row from that ordered result set

## Aggregate Functions and GROUP BY Clause

- Aggregate Funcitons are used for calculations on a set of values, returning a single value
- Useful for efficiency, reducing resource consumption, and performing calculations on a set of values without retrieving all the data

Example of most commonly used aggregate functions:
- `AVG()`: Returns the average value 
- `COUNT()`: Returns the number of rows
- `FIRST()`: Returns the first value   
- `LAST()`: Returns the last value    
- `MAX()`: Returns the largest value 
- `MIN()`: Returns the smallest value
- `SUM()`: Returns the sum 
- `COUNT(*)`: Returns the number of rows in the result set

For Code: `SELECT FirstName, COUNT(*) FROM Employees GROUP BY FirstName ORDER BY COUNT(*) ASC;`
It returns:
```
Lisa|1
Mark|1
Robert|1
John|3
```
Because it groups the result set by the FirstName column, returns the number of employees for each group and sorts the groups in descending order by the number of employees

The `GROUP BY` Clause is used to group the result set by one or more columns
  - Often combined with aggregate functions
  - Helps analyze and summarize data based on specific criteria
  - Allows sorting and ordering of grouped results

## HAVING Clause

- The `HAVING` Clause is used to filter groups in the result set based on conditions
- Often combined with aggregate functions like AVG(), COUNT(), MAX(), MIN(), and SUM()
- Enables the filtering of grouped results, allowing us to specify conditions for including or excluding groups
- Useful for refining the analysis of grouped data

## Introduction to JOINS

- A join clause combines rows from two or more tables based on a related column
- Foreign keys establish relationships between tables because it is is a column or a group of columns in a table that uniquely identifies a row in another table
  - One-to-many relationships allow one row in one table to be related to many rows in another table

For Code:
```
CREATE TABLE Employees (
    EmployeeID int,
    LastName varchar(255),
    FirstName varchar(255),
    DepartmentID int,
    BirthDate date,
    Notes text,
    Salary float
);

CREATE TABLE Departments (
    DepartmentID int,
    DepartmentName varchar(255),
    ManagerID int,
    Location varchar(255),
    Budget float,
    Notes text,
    Employees int
);

INSERT INTO Employees (EmployeeID, LastName, FirstName, DepartmentID, BirthDate, Notes, Salary)
VALUES (1, 'Doe', 'John', 1, '1990-01-01', 'John Doe was born on January 1, 1990.', 50000);
INSERT INTO Employees (EmployeeID, LastName, FirstName, DepartmentID, BirthDate, Notes, Salary)
VALUES (2, 'Doe', 'Jane', 1, '1991-02-02', 'Jane Doe was born on February 2, 1991.', 60000);

INSERT INTO Departments (DepartmentID, DepartmentName, ManagerID, Location, Budget, Notes, Employees)
VALUES (1, 'Sales', 1, 'New York', 1000000, 'The Sales department is located in New York.', 10);
INSERT INTO Departments (DepartmentID, DepartmentName, ManagerID, Location, Budget, Notes, Employees)
VALUES (2, 'Marketing', 2, 'Los Angeles', 2000000, 'The Marketing department is located in Los Angeles.', 20);

SELECT * FROM Employees, Departments;
```
Returns:
```
1|Doe|John|1|1990-01-01|John Doe was born on January 1, 1990.|50000|1|Sales|1|New York|1000000|The Sales department is located in New York.|10
1|Doe|John|1|1990-01-01|John Doe was born on January 1, 1990.|50000|2|Marketing|2|Los Angeles|2000000|The Marketing department is located in Los Angeles.|20
2|Doe|Jane|1|1991-02-02|Jane Doe was born on February 2, 1991.|60000|1|Sales|1|New York|1000000|The Sales department is located in New York.|10
2|Doe|Jane|1|1991-02-02|Jane Doe was born on February 2, 1991.|60000|2|Marketing|2|Los Angeles|2000000|The Marketing department is located in Los Angeles.|20
```

### Cross Join

- A cross join "also known as a Cartesian join" returns all possible combinations of rows from two tables
- It's formed using the `,` *"comma"* syntax but isn't often used due to its expansive result set
- An example is the code above

### Inner Join

- An inner join is a clause that combines rows from two or more tables and returns rows when there is a match in both tables
- It's the intersection of two tables, and it's useful for extracting related information

So code: 
`SELECT * FROM Employees INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;`
Returns:
```
1|Doe|John|1|1990-01-01|John Doe was born on January 1, 1990.|50000|1|Sales|1|New York|1000000|The Sales department is located in New York.|10
2|Doe|Jane|1|1991-02-02|Jane Doe was born on February 2, 1991.|60000|1|Sales|1|New York|1000000|The Sales department is located in New York.|10
```

## Left Join

- A left join returns all rows from the left table and matched rows from the right table
- It includes unmatched rows from the left table with null values for right table columns

So Code:
```
# Change the DepartmentID of the first employee to 3
INSERT INTO Employees (EmployeeID, LastName, FirstName, DepartmentID, BirthDate, Notes, Salary)
VALUES (1, 'Doe', 'John', 3, '1990-01-01', 'John Doe was born on January 1, 1990.', 50000);
.
.
.
SELECT * FROM Employees LEFT JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```
Returns:
```
1|Doe|John|3|1990-01-01|John Doe was born on January 1, 1990.|50000||NULL|NULL|NULL|NULL|NULL|NULL
2|Doe|Jane|1|1991-02-02|Jane Doe was born on February 2, 1991.|60000|1|Sales|1|New York|1000000|The Sales department is located in New York.|10
```
- **ON Employees.DepartmentID = Departments.DepartmentID** is a clause that specifies the columns that we want to join
  - There is no department with an ID of 3, since the first employee's departmentID is 3, the left join returns null values for the department columns

## Right Join

- A right join combines rows from two or more tables and returns all rows from the right table and matched rows from the left table
- It includes unmatched rows from the right table with null values for left table columns

## Full Join

- A full join returns all rows when there is a match in one of the tables
- It includes unmatched rows from both tables

## Self Join

- A self join is used to join a table to itself
- It's useful when working with hierarchical data or comparing rows within the same table

So for Code:
`SELECT * FROM Employees e1 INNER JOIN Employees e2 ON e1.DepartmentID = e2.DepartmentID;`
Returns:
```
1|Doe|John|3|1990-01-01|John Doe was born on January 1, 1990.|50000|1|Doe|John|3|1990-01-01|John Doe was born on January 1, 1990.|50000
2|Doe|Jane|1|1991-02-02|Jane Doe was born on February 2, 1991.|60000|2|Doe|Jane|1|1991-02-02|Jane Doe was born on February 2, 1991.|60000
```

- *e1 and e2* are aliases for the Employees table
  - **ON e1.DepartmentID = e2.DepartmentID** is a clause that specifies the columns that we want to join

## Overview of the Lesson

Databases can be categorized into two main types: 
- relational: stores data in tables
- non-relational: stores data in other ways

SQL being a language used to interact with relation databases
Important Concepts :

- CREATE TABLE: Creates a table in a database

- INSERT INTO: Inserts new rows into a table

- SELECT: Retrieves data from a database

- WHERE: Filters the result set based on specified conditions

- ORDER BY: Sorts the result set

- LIMIT: Restricts the number of rows in the result set

- GROUP BY: Groups the result set based on specified columns

- HAVING: Filters groups in the result set

- INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN: Combine rows from two or more tables

- SELF JOIN: Combines rows from the same table

- Aggregate Functions like "AVG(), COUNT()":
  - AVG(): Returns the average value
  - COUNT(): Returns the number of rows

and so on , but these are the important ones to remember from the many concepts we will come across