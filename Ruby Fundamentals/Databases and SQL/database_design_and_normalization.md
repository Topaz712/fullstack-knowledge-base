# Database Design and Normalization

- `Database Design`:
  - The process of designing a database schema, which is a collection of tables related to each other, often referred to as a relational database
 - The main purspose of a database schema is to define the structure of a database like the tables, columns, data types and relationships between tables while also defining constraints to apply to the data

- `Constraints`: 
  - Applied to the data to maintain accuracy and consistency
  - Constraint types are Table Level or Column Level
  -  Constraint types are unique in being exclusively defined at the column level, while `DEFAULT` constraints offer the option to be specified at either the column or table level

  - `NOT NULL`:
    - Defined at the column level
    - Ensures that a column cannot contain NULL values
      - It requires each row to have a valid "non-NULL" value for that column

This is like having: 
  - `PRIMARY KEY`:
    - Table-level constraint
    - Can include one or more columns
    - Guarantees unique combinations of values by having designated key columns in each row 
    - Prohibits null values in key columns

  - `FOREIGN KEY`:
    - Vital for maintaining referential integrity
    - A column that references a column in another table
      - Used to establish a relationship between two tables
    - Created in child tables
      - Associates each child row with one parent row
    - Requires uniqueness in referenced columns of the parent table like **UNIQUE or PRIMARY KEY** constraint
    - When wanting to `INSERT/UPDATE`, it ensures values in foreign key columns exist exactly once in the parent table
    - When wanting to `DELETE`, it verifies the absence of child rows before allowing deletion of a parent row
    - This is like having a child table called `Order` referencing the parent table called `Product`
      - *Product's UNIQUE or PRIMARY KEY* is referenced by the *Order's FOREIGN KEY*

Example of many to many relationship because one product can be in many orders and one order can have many products, using this: 
```
CREATE TABLE products (
  id INTEGER PRIMARY KEY,
  name TEXT,
  price REAL
);

CREATE TABLE orders (
  id INTEGER PRIMARY KEY,
  customer_id INTEGER,
  FOREIGN KEY (customer_id) REFERENCES customers(id)
);

CREATE TABLE order_items (
  id INTEGER PRIMARY KEY,
  order_id INTEGER,
  product_id INTEGER,
  FOREIGN KEY (order_id) REFERENCES orders(id),
  FOREIGN KEY (product_id) REFERENCES products(id)
);
```
Then to query the database to get all the products that are in an order, do:
```
SELECT * FROM products
WHERE id IN (
  SELECT product_id FROM order_items
  WHERE order_id = 1
);
```
That used a subquery to get all the products that are in order 1:
Returns:
```
id          name      price
----------  --------  ----------
1           Product 1  10.0
2           Product 2  20.0
```

  - `UNIQUE KEY`:
    - Table-level constraint
    - Can include one or more columns
    - Ensures uniqueness of values within a row
    - Multiple unique keys allowed in a table
    - This guarantees values won't repeat across rows
    - Enforces business rules requiring distinct values, allowing us to tailor constraints to business needs
    - Prevents duplication of specific data combinations

  - `CHECK`:
    - It is for setting up a logical condition that acts as a rule
      - This condition gets checked automatically every time we insert or update a row
      - If the condition is FALSE, it triggers an error
    - Ensures data meets specific criteria and provides error feedback when conditions are not met

  - `DEFAULT`:
    - Lets us set a default value for a column
    - If we forget to provide data for that column during an **INSERT**, the database will use our predefined value automatically
      -  If there's no **DEFAULT** defined and we skip the column, the database will just assign a NULL value
  - `NOT NULL`

- `Relational Database`: 
  - A collection of tables where each table represents an entity, each row represents an instance of that entity, and columns represent attributes with data types and default values

- `Normalization`:
  - The process of organizing data in a database to reduce data redundancy and improve data integrity
  - Important since, it ensures accurate and consistent data
  - There are different types of Normalization, such as:
    - *First Normal Form (1NF)*:
      - Ensures data is atomic, meaning each attribute contains only one value 
      - This reduces complexity and improves efficiency in querying and updating the database
        - An example: Instead of having a non-atomic table with multiple values in one attribute like a Students table with address as an attribute, we create separate tables, one for Person and one for Addresses to maintain atomicity, like so:
        - 
      ```
        CREATE TABLE students (
        id INTEGER PRIMARY KEY,
        first_name TEXT,
        last_name TEXT,
        grade INTEGER
      );

      CREATE TABLE addresses (
        id INTEGER PRIMARY KEY,
        student_id INTEGER,
        street TEXT,
        city TEXT,
        state TEXT,
        zip_code TEXT,
        FOREIGN KEY (student_id) REFERENCES students(id)
      );

      CREATE TABLE phone_numbers (
        id INTEGER PRIMARY KEY,
        student_id INTEGER,
        phone_number TEXT,
        FOREIGN KEY (student_id) REFERENCES students(id)
      );
      ```

    - *Second Normal Form (2NF)*:
      - Builds on 1NF and eliminates partial dependencies *making sure attributes are fully dependent on the primary key*
        - If attributes are unrelated to the primary key, it can lead to inefficiency in updates and queries, as well as potential data integrity issues
        - In the example below we link the Students table to the Schools table using a foreign key (school_id)
          - This ensures that data is in the right place, making updates and queries more efficient
          - 
          ```
          CREATE TABLE students (
            id INTEGER PRIMARY KEY,
            first_name TEXT,
            last_name TEXT,
            grade INTEGER,
            school_id INTEGER,
            FOREIGN KEY (school_id) REFERENCES schools(id)
          );

          CREATE TABLE schools (
            id INTEGER PRIMARY KEY,
            name TEXT,
            address TEXT
          );
           ```

    - *Third normal form (3NF)*:
      - Builds on 2NF and aims to create a database structure where *attributes are directly dependent/linked to the primary key*
      - Helps eliminate redundancy, promoting a more streamlined and efficient database structure
        - For Example if a table where attributes like school_name, school_address, school_phone_number, and school_website are all dependent on the primary key (id) for table Student, it would be redundant as it necessitates multiple updates for each row, creating copies of the same data for each student, making it inefficient for a large number of students, so instead we create a separate schools table with attributes dependent on the primary key and link the students table to the schools table using a foreign key (school_id), this enhances efficiency by requiring fewer updates and allows easier querying of the database
        - 
        ```
        CREATE TABLE students (
          id INTEGER PRIMARY KEY,
          first_name TEXT,
          last_name TEXT,
          grade INTEGER,
          school_id INTEGER,
          FOREIGN KEY (school_id) REFERENCES schools(id)
        );

        CREATE TABLE schools (
          id INTEGER PRIMARY KEY,
          name TEXT,
          address TEXT,
          phone_number TEXT,
          website TEXT
        );
        ```
    - These other levels are less common and are used in special cases:
      - *Boyce-Codd normal form (BCNF)*
      - *Fourth normal form (4NF)*
      - *Fifth normal form (5NF)*
      - *Domain/key normal form (DKNF)*

**Things for considerations in Database Schema Designing are:**

- *Entities*:
  - Define what entities exist in the database

- *Attributes*:
  - Identify attributes for each entity, represented as columns in tables
  - Specify data types and default values for attributes like "INTEGER/NOT NULL"

- *Relationships*:
  - Identify and define relationships between different entities
  - Specify the cardinality of relationships like "1:1, 1:N, M:N, M:1" to describe the number of instances involved


`Cardinality`:
  - Refers to the number of instances of one entity related to another
  - Represented by symbols such as 1:1, 1:N, M:N, M:1

`Crow's Feet`:
  - In database modeling, crow's feet is a graphical representation of how entities relate to each other 
  - The lines from entities indicate how many of one thing connect to another 
  - It helps illustrate the connections between different parts of the database

*Cardinality Relationship Examples:*

- **One to One (1:1)**
  - One instance of A can be related to one instance of B
  - Example: A customer has only one mailing address

- **One to Many (1:N)**
  - One instance of A can be related to zero or more instances of B
  - Example: A customer can have multiple orders
  - Allows one instance on the left to be related to many instances on the right

- **One-to-One or One-to-Many (1:1..N)** 
  - One and only one instance of A can be related to one or more instances of B
  - One instance on the left side can be related to one or more instances on the right side
  - Example: One teacher "left" can have one or more students "right"
  - Allows one instance on the left to be related to one or more instances on the right

- **Many to Many (M:N)**
  - Zero or more instances of A can be related to zero or more instances of B
  - Example: A product can be in multiple orders, and an order can have multiple products

- **Many to One (M:1)/(N:1)**
  - Many instances on the left side can be related to one instance on the right side
  - Example: A product can be in multiple orders, but an order can only have one product or many employees "left" can belong to one department "right"
  -  Allows many instances on the left to be related to one instance on the right

- **One to Zero or One (1:0..1)**
  - One and only one instance of A can be related to zero or one instance of B
  - Example: A customer can have zero or one mailing address

- **One and Many to One and Many (1..M:1..N)**
  - One or more instances of A can be related to one or more instances of B
  - Example: A customer can have one or more orders, and an order can have one or more products
