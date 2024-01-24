# Practice Problems for Database Fundamentals Part 2

1. 
Create a table called users with the following columns:

id
first_name
last_name
email
password
Insert 3 users into the table. Here are the there users

| first_name | last_name | email | password | | ---------- | --------- | ----------------- | -------- | | John | Doe | johndoe@gmail.com | password | | Jane | Doe | janedoe@gmail.com | password | | Sally | Smith | sallysmith@gmail | password |

Update the email of the user with the id of 1 to updatedemail@gmail.com

Delete the user with the id of 2.

Print all the users in the table.
```
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  first_name TEXT,
  last_name TEXT,
  email TEXT,
  password TEXT
);

INSERT INTO users (first_name, last_name, email, password)
VALUES ('John', 'Doe', 'johndoe@gmail.com', 'password');
INSERT INTO users (first_name, last_name, email, password)
VALUES ('Jane', 'Doe', 'janedoe@gmail.com`', 'password');
INSERT INTO users (first_name, last_name, email, password)
VALUES ('Sally', 'Smith', 'sallysmith@gmail', 'password');

UPDATE users
SET email = 'updatedEmail@gmail.com'
WHERE id = 1;

DELETE FROM users
WHERE id = 2;

SELECT * FROM users;
```

2. 
Let's take a moment to develop relationships between schools and students.

What are the entities in the database?
What are the attributes of each entity?
What are the relationships between the entities?
What are the cardinalities of the relationships?

Solution:

*What are the entities in the database?*
- Schools
- Students

*What are the attributes of each entity?*
- Schools
  - id
  - name
  - address
  - phone_number
  - email
  - website
  - number_of_students
- Students
  - id
  - first_name
  - last_name
  - grade
  - school_id

*What are the cardinalities of the relationships?*
- Schools to Students: (1:N)
  - One to many
- Students to Schools: (N:1)
  - Many to one
 
3. 
Let's take a moment to normalize the following table.

CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  first_name TEXT,
  last_name TEXT,
  email TEXT,
  password TEXT,
  addresses TEXT,
  phone_numbers TEXT
);

Answer:

```
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  first_name TEXT,
  last_name TEXT,
  email TEXT,
  password TEXT
);

CREATE TABLE addresses (
  id INTEGER PRIMARY KEY,
  user_id INTEGER,
  street TEXT,
  city TEXT,
  state TEXT,
  zip_code TEXT,
  FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE phone_numbers (
  id INTEGER PRIMARY KEY,
  user_id INTEGER,
  phone_number TEXT,
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```