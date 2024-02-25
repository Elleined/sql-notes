# sql-notes
Notes for SQL

# 2 Database Components
### Client
- MySQL Workbench
- SQL Command Line Client
### Server
- SQL Server: the one that will be installed in you local machine thats why we can have multiple clients connected to server remotely or locally.

# 5 SQL Command Categories
## TCL (Transaction Control Languange)
- Used to control beginning and end of sql transaction to ensure consistency and integrity of data.

### Commands
- ROLLBACK
- COMMIT
- SAVEPOINT

## DML (Data Manipulation Languange)
- Used to manage and manipulate the data in database table like inserting new record, updating existing record, and deleting existing record.

### Commands
###### UPDATE  
```
UPDATE table_name
SET column_name = <new_value>
WHERE condition
```
###### DELETE
```
DELETE FROM table_name
WHERE condition
```
###### INSERT
- ###### Without specified columns
```
INSERT INTO table_name
VALUES (...)
```
- ###### With specified columns
```
INSERT INTO table_name (column1, column2, ...)
VALUES (val1, val2, ...)
```
- ###### Multiple record in single query
```
INSERT INTO table_name (column1, column2, ...)
VALUES
(val1, val2, ...),
(val1, val2, ...),
(val1, val2, ...)
```

## DDL (Data Definition Languange)
- Used to define and manage database schema/ structure.

### Commands
###### CREATE
```
CREATE TABLE table_name (
id INT AUTO_INCREMENT PRIMARY KEY,
column_name1 datatype1,
column_name2 datatype2
);
```
###### DROP
```
DROP TABLE table_name
```
###### TRUNCATE
```
TRUNCATE TABLE table_name
```
###### ALTER
- ###### Add column
```
ALTER TABLE table_name ADD COLUMN column_name data_type
```
- ###### Drop column
```
ALTER TABLE table_name DROP COLUMN column_name
```
- ###### Rename column name
```
ALTER TABLE table_name RENAME COLUMN old_column_name TO new_column_name
```
###### RENAME
```
RENAME TABLE old_table_name TO new_table_name
```

## DQL (Data Query Languange)
- Used to read/ retrieve a record in database table.

### Commands
###### SELECT
- ###### Without specified columns
```
SELECT * FROM table_name
```
- ###### With specified columns
```
SELECT column1, column2, ... FROM table_name
```

## DCL (Data Control Languange)
- Used to control access to database schema and privileges to different users to control security and permissions.

### Commands
- GRANT
- REVOKE

# 5 Aggregate Function
- **SUM(column_name)**
- **AVG(column_name)**
- **MIN(column_name)**
- **MAX(column_name)**
- **COUNT(column_name)**

# Data Types
## Text Data Types
##### String
- VARCHAR(size)
- CHAR(size)
- ENUM(val1, val2, val3, ...)

##### Text
- TEXT
- TINYTEXT
- MEDIUMTEXT
- LONGTEXT

##### Blob 
- BLOB
- TINYBLOB
- MEDIUMBLOB
- LONGBLOB

## Numeric Data Types
- FLOAT
- DECIMAL
- DOUBLE

##### INT
- INT
- TINYINT
- MEDIUMINT
- BIGINT

## Date and Time Data Types
- DATE
- TIME
- DATETIME
- TIMESTAMP

# Operators
## Special Operators
- **ALL**: returns all the rows of table if all the values match to table data.
```
SELECT column_name
FROM table_name
WHERE column_name
ALL condition
```
- **IN**: returns all the rows of table if the given values match with table data.
```
SELECT column_name
FROM table_name
WHERE column_name
IN (val1, val2, val...)
```
- **ANY**: returns all the rows of table if any of the values match with table data.
```
SELECT column_name
FROM table_name
WHERE column_name <comparison operator> ANY(val1, val2, ...)
```
- **LIKE**: returns all the rows of table if given pattern match with table data.
  ###### Different like pattern matching
  - **'string%'**: means starting with given string.
  - **'%string'**: means ending with given string.
  - **'%string%'**: means any record containing the string.
```
SELECT column_name
FROM table_name
WHERE column_name
LIKE '%string%'
```
- **BETWEEN**: returns all of the rows of table if the specified range of values match with table data.
```
SELECT column_name
FROM table_name
WHERE column_name
BETWEEN <starting_value> AND <ending_value>
```
- **IS NULL**: returns all of the rows of table if specified column value is null.
```
SELECT column_name
FROM table_name
WHERE column_name IS NULL
```

## Logical Operators
- **AND**: returns all of the rows of table if condition1 and condition2 are both true.
```
SELECT column_name
FROM table_name
WHERE condition1 AND condition2
```
- **OR**: returns all of the rows of table if either condition1 and condition2 are true.
```
SELECT column_name
FROM table_name
WHERE condition1 OR condition2
```
- **NOT**: returns all of the rows of table that doesn't match with table data to the given condition.
```
SELECT column_name
FROM table_name
WHERE column_name NOT NULL
```

## Comparison Operators
- **>**: Greater than
- **>=**: Greater than or equal to
- **!>**: Not greater than

- **<**: Less than
- **<=**: Less tham or equal to
- **!<**: Not less than

- **=**: Equal to
- **!=**: Not equal to
- **<>**: Not equal to

# Clauses
- **DISTINCT**: Used to remove all the duplicate values in returned rows.
```
SELECT DISTINCT column_name
FROM table_name
```
- **LIMIT**: Used to limit the returned rows with specified number of rows you want.
```
SELECT column_name
FROM table_name
LIMIT <number_of_rows>
```
- **WHERE**: Used to perform condition based query.
```
SELECT column_name
FROM table_name
WHERE <condition>
```
- **ORDER BY**: Used to sort the returned rows via specified column with ascending as default.
```
SELECT column_name
FROM table_name
ORDER BY column_name
```
# Keys
###### Primary Key
- A value that uniquely identifies a record/ row.
###### Foreign Key
- A primary key of table that is used in another table.
###### Candidate Key
- A value that can be choosen as primary key also.
###### Alternate Key
- A candidate key that is not choosen as primary key.
###### Surrogate Key
- A system generated-value as primary key.
# Joins
# Index
- Is a BTREE data structure that allows you to search faster.
```
CREATE INDEX index_name
ON table_name (column_name...)
```
##### Index Advantage
- [x] Make SELECT statement faster
- [x] Make Filtering and sorting faster
##### Index Disadvantage
- [x] Make INSERT, DELETE, and UPDATE slower
###### Because adding indexes takes up storage just like the indexing in the book it makes searching easier with help of indec but inserting, deleting, and updating of content will become slower because you need to adjust all the index and it also consume more pages making it heavy same thing with MySQL index.

# Function
- Used to passed a argument then strictly return single row.
```
DELIMITER // 
CREATE FUNCTION function_name (parameter1, parameter2, ...)
RETURNS datatype DETERMINISTIC
BEGIN
     DECLARE variable_name datatype;
     <query result> INTO variable_name
     RETURN variable_name;
END //
DELIMITER ;
```
###### Notes
- You cannot use stored procedure inside function
- Can only return strictly one row.
- Commonly used to passed a primary key to return single value from primary key row.
# Stored Procedure
- Used to have pre-compiled query that can be executed for repititive task.
```
DELIMITER //
CREATE PROCEDURE procedure_name (
IN parameter1 datatype1,
IN parameter2 datatype2)
BEGIN
     // Code here
END //

DELIMITER ;
```

###### Notes
- You can used function inside stored procedure.
- You can return multiple rows in stored procedure.
- Stored procedure is also used for security and access control.
# Views
- Is a virtual table that is based on the result set of the real table. Any modifications in a real table will also affect the views. Basically views are like creating a virtual table that is branching out from the real table and can also be interacted just like a real table.
  
- Commonly used in SELECT statements. becuase as you realize stored procedure is used commonly in UPDATE and DELETE or DML commands and  views is used in SELECT or DQL commands.

### Why use view
- Restrict the user from seeing the real table structure thus adding extra layer of security.
- Abstracts/ Simplify the complex query returned from the complex real table and complex table joinings.

### Views Restrictions
- Cannot create index in views.
- Cannot create trigger in views.

# Triggers

# Fulltext search
- Used to easily search text block inside table column.
```
-- First alter the table
ALTER TABLE table_name ADD FULLTEXT(columns...)

-- Now when you query
SELECT column_name(s)
FROM table_name
WHERE MATCH (columns_with_fulltext_index)
AGAINST (value_you_want_to_search)
```

###### Fulltext Support
- ###### +: Means keyword must be present in each row returned.
- ###### -: Means keyword must not be in each row returned.
- ###### *: Serves as wildcard
- ###### ": Means MySQL will literally search the table with the exact phrase.

### Copy table data into another table
```
INSERT INTO new_table_name (columns...)
SELECT column_names_to_be_copied
FROM table_to_be_copied
```
### [How to backup and restore database](https://github.com/Elleined/mysql-backup-script)

