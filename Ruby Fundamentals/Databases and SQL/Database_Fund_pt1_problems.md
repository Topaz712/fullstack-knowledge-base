# Practice Problems for Database Fundamentals Lesson Part 1

1. 
Create a table named Students with the following columns:
  - StudentID is an integer
  - LastName is a variable-length character string 
  - FirstName is a variable-length char string 
  - BirthDate is a date value
  - Notes is a long text string
  - GPA is a floating-point number
  - Major is a variable-length char string

answer:
```
CREATE TABLE Students (
  StudentID int,
  LastName varchar(255),
  FirstName varchar(255),
  Birthdate date,
  Notes text,
  GPA float,
  Major varchar(255)
);
```

Insert the following rows into the Students table:

StudentID is 1, LastName is Doe, FirstName is John, BirthDate is 1990-01-01, Notes is John Doe was born on January 1, 1990., GPA is 3.5, Major is Computer Science

StudentID is 2, LastName is Doe, FirstName is Jane, BirthDate is 1991-02-02, Notes is Jane Doe was born on February 2, 1991., GPA is 3.6, Major is Computer Science

answer:
```
INSERT INTO Students (StudentID, LastName, FirstName, BirthDate, Notes, GPA, Major)
VALUES (1, 'Doe', 'John', '1990-01-01', 'John Doe was born on January 1, 1990.', 3.5, 'Computer Science');

INSERT INTO Students (StudentID, LastName, FirstName, BirthDate, Notes, GPA, Major)
VALUES (2, 'Doe', 'Jane', '1991-02-02', 'Jane Doe was born on February 2, 1991.', 3.6, 'Computer Science');
```

Select all rows from the Students table where the Major is equal to Computer Science and the GPA is greater than or equal to 3.5. Sort the result set in descending order by the GPA column. Limit the result set to 1 row.

answer:
`SELECT * FROM Students WHERE Major = 'Computer Science' AND GPA >= 3.5 ORDER BY GPA DESC LIMIT 1;`

2. 
Create a table named Students with the following columns:

StudentID is an integer number that uniquely identifies each student
LastName is a variable-length character string that stores the last name of the student
FirstName is a variable-length character string that stores the first name of the student
BirthDate is a date value that stores the birth date of the student
Notes is a long text string that stores notes about the student
GPA is a floating-point number that stores the grade point average of the student

answer:
```
CREATE TABLE Students (
    StudentID int,
    LastName varchar(255),
    FirstName varchar(255),
    BirthDate date,
    Notes text,
    GPA float
);
```

Insert the following rows into the Students table:

StudentID is 1, LastName is Doe, FirstName is John, BirthDate is 1990-01-01, Notes is John Doe was born on January 1, 1990., GPA is 3.5
StudentID is 2, LastName is Doe, FirstName is Jane, BirthDate is 1991-02-02, Notes is Jane Doe was born on February 2, 1991., GPA is 3.6
StudentID is 3, LastName is Moe, FirstName is John, BirthDate is 1992-03-03, Notes is Mary Doe was born on March 3, 1992., GPA is 3.7
StudentID is 4, LastName is Doe, FirstName is Mark, BirthDate is 1993-04-04, Notes is Mark Doe was born on April 4, 1993., GPA is 3.8
StudentID is 5, LastName is Doe, FirstName is Lisa, BirthDate is 1994-05-05, Notes is Lisa Doe was born on May 5, 1994., GPA is 3.9

```
INSERT INTO Students (StudentID, LastName, FirstName, BirthDate, Notes, GPA)
VALUES (1, 'Doe', 'John', '1990-01-01', 'John Doe was born on January 1, 1990.', 3.5);
INSERT INTO Students (StudentID, LastName, FirstName, BirthDate, Notes, GPA)
VALUES (2, 'Doe', 'Jane', '1991-02-02', 'Jane Doe was born on February 2, 1991.', 3.6);
INSERT INTO Students (StudentID, LastName, FirstName, BirthDate, Notes, GPA)
VALUES (3, 'Moe', 'John', '1992-03-03', 'Mary Doe was born on March 3, 1992.', 3.7);
INSERT INTO Students (StudentID, LastName, FirstName, BirthDate, Notes, GPA)
VALUES (4, 'Doe', 'Mark', '1993-04-04', 'Mark Doe was born on April 4, 1993.', 3.8);
INSERT INTO Students (StudentID, LastName, FirstName, BirthDate, Notes, GPA)
VALUES (5, 'Doe', 'Lisa', '1994-05-05', 'Lisa Doe was born on May 5, 1994.', 3.9);
```

Select all rows from the Students table and return the average GPA of all students. Group the result set by the FirstName column and return the average GPA for each group. Filter the groups that have more than 1 student. Sort the groups in descending order by the average GPA.

answer:
`SELECT FirstName, AVG(GPA) FROM Students GROUP BY FirstName HAVING COUNT(*) > 1 ORDER BY AVG(GPA) DESC;`


3. 
Imagine you have a database for a bookstore. The database includes the following tables:

Authors: Contains data about authors.
Columns: AuthorID (primary key), AuthorName

Books: Contains data about books.
Columns: BookID (primary key), Title, AuthorID (foreign key), PublicationYear

Sales: Contains data about book sales.
Columns: SaleID (primary key), BookID (foreign key), QuantitySold, SaleDate

```
CREATE TABLE Authors (
  AuthorID int PRIMARY KEY,
  AuthorName varchar(255)
);

CREATE TABLE Books (
  BookID int PRIMARY KEY,
  Title varchar(255),
  AuthorID int,
  PublicationYear int
);

CREATE TABLE Sales (
  SaleID int PRIMARY KEY,
  BookID int,
  QuantitySold int,
  SaleDate date
);

INSERT INTO Authors (AuthorID, AuthorName)
VALUES (1, 'F. Scott Fitzgerald');
INSERT INTO Authors (AuthorID, AuthorName)
VALUES (2, 'Ray Bradbury');

INSERT INTO Books (BookID, Title, AuthorID, PublicationYear)
VALUES (1, 'The Great Gatsby', 1, 1925);
INSERT INTO Books (BookID, Title, AuthorID, PublicationYear)
VALUES (2, 'Fahrenheit 451', 2, 1953);

INSERT INTO Sales (SaleID, BookID, QuantitySold, SaleDate)
VALUES (1, 1, 10, '1925-04-10');
INSERT INTO Sales (SaleID, BookID, QuantitySold, SaleDate)
VALUES (2, 1, 20, '1953-10-19');
```

Task 
Write SQL queries to perform the following tasks:

List of Books and Authors:
Write a query to display a list of all books, including their titles and the names of their authors. Use an INNER JOIN to combine data from the Books and Authors tables.

answer:
`SELECT * FROM Books INNER JOIN Authors ON Books.AuthorID = Authors.AuthorID;`

Books with No Sales:
Write a query to find all books that have never been sold. Use a LEFT JOIN between Books and Sales and look for records where there are no corresponding sales entries.

answer:
`SELECT * FROM Books LEFT JOIN Sales ON Books.BookID = Sales.BookID WHERE Sales.BookID IS NULL;`

Total Sales for Each Book:
Write a query to calculate the total quantity sold for each book. Use an INNER JOIN to combine Books and Sales, and then use a GROUP BY clause with an aggregate function (SUM) to calculate total sales.

answer:
`SELECT Title, SUM(QuantitySold) FROM Books INNER JOIN Sales ON Books.BookID = Sales.BookID GROUP BY Title;`

Sales Data for a Specific Year:
Write a query to display the sales data (book title and quantity sold) for all books sold in a specific year (e.g., 2021). This will require joining all three tables and filtering based on SaleDate.

answer:
`SELECT Title, QuantitySold FROM Books INNER JOIN Sales ON Books.BookID = Sales.BookID WHERE YEAR(SaleDate) = 1953;`
