# Exercise 1

Objective: Retrieve all data from the Products table.
Table: Products
Columns: ProductID (int), ProductName (text), Price (float), Category (text)
Data:
(1, 'Laptop', 1200.00, 'Electronics')
(2, 'Desk Chair', 250.50, 'Furniture')
The expected outcome should be

| ProductID | ProductName | Price  | Category    |
| --------- | ----------- | ------ | ----------- |
| 1         | Laptop      | 1200.0 | Electronics |
| 2         | Desk Chair  | 250.5  | Furniture   |

```
CREATE TABLE Products(
    ProductID int,
    ProductName varchar(255),
    Price float,
    Category varchar(255)
);

INSERT INTO Products (ProductID, ProductName, Price, Category) VALUES (1, 'Laptop', 1200.00, 'Electronics');
INSERT INTO Products (ProductID, ProductName, Price, Category) VALUES (2, 'Desk Chair', 250.50, 'Furniture');

SELECT * FROM Products;

```

# Exercise 2

Objective: Select only the FirstName and LastName columns from the Employees table.
Table: Employees
Columns: EmployeeID (int), FirstName (text), LastName (text), Department (text)
Data:
(1, 'Alice', 'Johnson', 'HR')
(2, 'Bob', 'Smith', 'IT')
The expected outcome should be

| FirstName | LastName |
| --------- | -------- |
| Alice     | Johnson  |
| Bob       | Smith    |

```
CREATE TABLE Employees(
    EmployeeID int,
    FirstName varchar(255),
    LastName varchar(255),
    Department varchar(255)
);

INSERT INTO Employees(EmployeeID, FirstName, LastName, Department) VALUES (1, 'Alice', 'Johnson', 'HR');
INSERT INTO Employees(EmployeeID, FirstName, LastName, Department) VALUES (2, 'Bob', 'Smith', 'IT');

SELECT FirstName, LastName From Employees;
```

# Exercise 3

Objective: Display details of items in the Inventory table that have less than 20 units in stock.
Table: Inventory
Columns: ItemID (int), ItemName (text), UnitsInStock (int)
Data:
(1, 'Printer Paper', 15)
(2, 'Staples', 30)
The expected outcome should be

| ItemID | ItemName      | UnitsInStock |
| ------ | ------------- | ------------ |
| 1      | Printer Paper | 15           |

```
CREATE TABLE Inventory(
    ItemID int,
    ItemName varchar(255),
    UnitsInStock int
);

INSERT INTO Inventory (ItemID, ItemName, UnitsInStock) VALUES (1, 'Printer Paper', 15);
INSERT INTO Inventory (ItemID, ItemName, UnitsInStock) VALUES (2, 'Staples', 30);

SELECT * FROM Inventory WHERE UnitsInStock < 20;
```

# Exercise 4

Objective: Retrieve all data from the Books table.
Table: Books
Columns: BookID (int), Title (text), Author (text), Price (float)
Data:
(1, 'The Great Gatsby', 'F. Scott Fitzgerald', 10.99)
(2, '1984', 'George Orwell', 8.99)
(3, 'The Catcher in the Rye', 'J. D. Salinger', 7.99)
The expected outcome should be

| BookID | Title                  | Author              | Price |
| ------ | ---------------------- | ------------------- | ----- |
| 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 |
| 2      | 1984                   | George Orwell       | 8.99  |
| 3      | The Catcher in the Rye | J. D. Salinger      | 7.99  |

```
CREATE TABLE Books(
    BookID int,
    Title varchar(255),
    Author varchar(255),
    Price float
);

INSERT INTO Books(BookID, Title, Author, Price) VALUES (1, 'The Great Gatsby', 'F. Scott Fitzgerald', 10.99);
INSERT INTO Books(BookID, Title, Author, Price) VALUES (2, '1984', 'George Orwell', 8.99);
INSERT INTO Books(BookID, Title, Author, Price) VALUES (3, 'The Catcher in the Rye', 'J. D. Salinger', 7.99);

SELECT * FROM Books;
```

# Exercise 5

Objective: Display the course names and their corresponding department from the Courses table.
Table: Courses
Columns: CourseID (int), CourseName (text), Department (text), Credits (int)
Data:
(101, 'Introduction to Psychology', 'Psychology', 3)
(102, 'Principles of Economics', 'Economics', 4)
(103, 'Introduction to Computer Science', 'Computer Science', 3)
The expected outcome should be

| CourseName                       | Department       |
| -------------------------------- | ---------------- |
| Introduction to Psychology       | Psychology       |
| Principles of Economics          | Economics        |
| Introduction to Computer Science | Computer Science |

```
CREATE TABLE Courses(
   CourseID int,
   CourseName varchar(255),
   Department varchar(255),
   Credits int
);

INSERT INTO Courses(CourseID, CourseName, Department, Credits) VALUES (101, 'Introduction to Psychology', 'Psychology', 3);
INSERT INTO Courses(CourseID, CourseName, Department, Credits) VALUES (102, 'Principles of Economics', 'Economics', 4);
INSERT INTO Courses(CourseID, CourseName, Department, Credits) VALUES (103, 'Introduction to Computer Science', 'Computer Science', 3);

SELECT CourseName, Department FROM Courses;
```

# Exercise 6

Objective: Retrieve the names of restaurants that have received a rating of "Excellent".
Table: RestaurantReviews
Columns: ReviewID (int), RestaurantName (text), Rating (text), Reviewer (text), ReviewDate (date)
Data:
(1, 'Cafe Mocha', 'Excellent', 'John Doe', '2022-01-15')
(2, 'Burger Corner', 'Good', 'Jane Smith', '2022-02-20')
(3, 'Pasta Place', 'Excellent', 'Alice Jones', '2022-02-22')
The expected outcome should be

| RestaurantName |
| -------------- |
| Cafe Mocha     |
| Pasta Place    |

```
CREATE TABLE RestaurantReviews (
    ReviewID int,
    RestaurantName varchar(255),
    Rating varchar(50),
    Reviewer varchar(255),
    ReviewDate date
);

INSERT INTO RestaurantReviews (ReviewID, RestaurantName, Rating, Reviewer, ReviewDate) VALUES
(1, 'Cafe Mocha', 'Excellent', 'John Doe', '2022-01-15'),
(2, 'Burger Corner', 'Good', 'Jane Smith', '2022-02-20'),
(3, 'Pasta Place', 'Excellent', 'Alice Jones', '2022-02-22');

SELECT RestaurantName FROM RestaurantReviews WHERE Rating = 'Excellent';
```

# Exercise 7

Objective: Find the total sales amount for each product.
Table: Sales
Columns: SaleID (int), ProductID (int), SaleAmount (float)
Data:
(1, 1, 1200.00)
(2, 2, 250.50)
The expected return should be the sum which is 1450.50

```
CREATE TABLE Sales (
    SaleID int,
    ProductID int,
    SaleAmount float
);

INSERT INTO Sales (SaleID, ProductID, SaleAmount) VALUES
(1, 1, 1200.00),
(2, 2, 250.50);

SELECT SUM(SaleAmount) from Sales;
```

# Exercise 8

Objective: Calculate the average price of all products in the Products table.
Table: Products
Columns: ProductID (int), ProductName (text), Price (float), Category (text)
Data:
(1, 'Apple', 0.50, 'Fruit')
(2, 'Bread', 1.50, 'Bakery')
The expected return should be the average which is 1.00

```
CREATE TABLE Products (
    ProductID int,
    ProductName varchar(255),
    Price float,
    Category varchar(255)
);

INSERT INTO Products (ProductID, ProductName, Price, Category) VALUES
(1, 'Apple', 0.50, 'Fruit'),
(2, 'Bread', 1.50, 'Bakery');

SELECT AVG(price) FROM Products;
```

# Exercise 9

Objective: Find the total quantity sold for a specific product such as the product with the id of 1 from the Sales table.
Table: Sales
Columns: SaleID (int), ProductID (int), QuantitySold (int), SaleDate (date)
Data:
(101, 1, 50, '2022-01-01')
(102, 2, 30, '2022-01-02')
(103, 1, 20, '2022-01-03')
The expected return should be the sum which is 70.

```
CREATE TABLE Sales (
    SaleID int,
    ProductID int,
    QuantitySold int,
    SaleDate date
);

INSERT INTO Sales (SaleID, ProductID, QuantitySold, SaleDate) VALUES
(101, 1, 50, '2022-01-01'),
(102, 2, 30, '2022-01-02'),
(103, 1, 20, '2022-01-03');

SELECT SUM(QuantitySold) FROM Sales WHERE ProductID = 1;
```

# Exercise 10

Objective: Retrieve the maximum and minimum temperature recorded in the WeatherData table.
Table: WeatherData
Columns: RecordID (int), Date (date), Temperature (float), City (text)
Data:
(1, '2022-01-01', 35.2, 'Springfield')
(2, '2022-01-01', 28.4, 'Shelbyville')

```
CREATE TABLE WeatherData (
    RecordID int,
    Date date,
    Temperature float,
    City varchar(255)
);

INSERT INTO WeatherData (RecordID, Date, Temperature, City) VALUES
(1, '2022-01-01', 35.2, 'Springfield'),
(2, '2022-01-01', 28.4, 'Shelbyville');

SELECT max(Temperature), min(Temperature) FROM WeatherData;
```

# Exercise 11

Objective: Show the product names and their corresponding order dates.
Tables:
Orders: OrderID (int), ProductID (int), OrderDate (date)
Products: ProductID (int), ProductName (text)
Data:
Orders: (1, 1, '2023-01-01'), (2, 2, '2023-01-02')
Products: (1, 'Laptop'), (2, 'Desk Chair')
The expected return should be

| ProductName | OrderDate  |
| ----------- | ---------- |
| Laptop      | 2023-01-01 |
| Desk Chair  | 2023-01-02 |

```
CREATE TABLE Orders (
    OrderID int,
    ProductID int,
    OrderDate date
);

CREATE TABLE Products (
    ProductID int,
    ProductName varchar(255)
);

INSERT INTO Orders (OrderID, ProductID, OrderDate) VALUES
(1, 1, '2023-01-01'),
(2, 2, '2023-01-02');

INSERT INTO Products (ProductID, ProductName) VALUES
(1, 'Laptop'),
(2, 'Desk Chair');

SELECT Products.ProductName, Orders.OrderDate FROM Products JOIN Orders ON Products.ProductID = Orders.ProductID;
```

# Exercise 12

Objective: Display the name of each employee and the name of the department they work in.
Tables:
Employees: EmployeeID (int), FirstName (text), LastName (text), DepartmentID (int)
Departments: DepartmentID (int), DepartmentName (text)
Data:
Employees: (1, 'Alice', 'Johnson', 1), (2, 'Bob', 'Smith', 2)
Departments: (1, 'HR'), (2, 'IT')

```
CREATE TABLE Employees (
    EmployeeID int,
    FirstName varchar(255),
    LastName varchar(255),
    DepartmentID int
);

CREATE TABLE Departments (
    DepartmentID int,
    DepartmentName varchar(255)
);

INSERT INTO Employees (EmployeeID, FirstName, LastName, DepartmentID) VALUES
(1, 'Alice', 'Johnson', 1),
(2, 'Bob', 'Smith', 2);

INSERT INTO Departments (DepartmentID, DepartmentName) VALUES
(1, 'HR'),
(2, 'IT');

SELECT Employees.FirstName, Employees.LastName, Departments.DepartmentName FROM Employees JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
```
