# Data Manipulation and Modification

_Data Manipulation and Modification is the process of adding, updating, and deleting data from a database_

The following SQL statements will get this done:

- `INSERT INTO`:

  - Adds data to a database
  - _Syntax_: `INSERT INTO` table_name (column1, column2, column3, ...) `VALUES` (value1, value2, value3, ...);
  - Inserts a new row into the table
  - Unspecified columns are filled with default values or NULL

- `UPDATE`:

  - Modifies existing data in a database
  - _Syntax_: `UPDATE` table_name `SET` column1 = value1, column2 = value2, ... `WHERE` condition;
  - Updates existing rows based on the specified condition
  - If the `WHERE` clause is omitted, all rows will be updated

- `DELETE`:

  - Removes existing data from a database
  - _Syntax_: `DELETE` `FROM` table_name `WHERE` condition;
  - Deletes rows based on the specified condition
  - If the `WHERE` clause is omitted, all rows will be deleted

For Code:

```
CREATE TABLE students (
  id INTEGER PRIMARY KEY,
  first_name TEXT,
  last_name TEXT,
  grade INTEGER
);

INSERT INTO students (first_name, last_name, grade)
VALUES ('John', 'Doe', 90);
INSERT INTO students (first_name, last_name, grade)
VALUES ('Jane', 'Doe', 95);
INSERT INTO students (first_name, last_name, grade)
VALUES ('Sally', 'Smith', 100);

SELECT * FROM students;
```

Returns:

```
id          first_name  last_name   grade
----------  ----------  ----------  ----------
1           John        Doe         90
2           Jane        Doe         95
3           Sally       Smith       100
```

**Example using the `UPDATE` statement:**

```
UPDATE students
SET grade = 100
WHERE first_name = 'John';

SELECT * FROM students;
```

Returns:

```
id          first_name  last_name   grade
----------  ----------  ----------  ----------
1           John        Doe         100
2           Jane        Doe         95
3           Sally       Smith       100
```

**Example using the `DELETE` statement:**

```
DELETE FROM students
WHERE first_name = 'John';

SELECT * FROM students;
```

Returns:

```
id          first_name  last_name   grade
----------  ----------  ----------  ----------
2           Jane        Doe         95
3           Sally       Smith       100
```
