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
- UPDATE
- DELETE
- INSERT

## DDL (Data Definition Languange)
- Used to define and manage database schema/ structure.

### Commands
- CREATE
- DROP
- TRUNCATE
- ALTER
- RENAME

## DQL (Data Query Languange)
- Used to read/ retrieve a record in database table.

### Commands
- SELECT

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
- **BETWEEN** 
- **IS NULL**

## Logical Operators
- **AND**
- **OR**
- **NOT**

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
# Keys
# Joins
# Index
# Function
# Stored Procedure

# Different ways to insert record in database table
