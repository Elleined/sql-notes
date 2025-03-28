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
- ###### RENAME
```
RENAME TABLE old_table_name TO new_table_name
```
- ###### Modify column
```
ALTER TABLE table_name
MODIFY COLUMN column_name new_data_type;
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

# Built-in Functions
- **Scalar Functions**: Operates in row level or we should say single row and returns single row. 
- **Aggregate Function**: Operates in column level or we should say multiple rows and returns single row. Also these functions are also used to access GROUP BY and HAVING clauses.  

## Scalar Functions
- **Numeric functions**
  - **ABS**: removes any sign of the number, thus returning the absolute number.
  ```sql
  SELECT ABS(-12.5)
  -- outputs 12.5
  ```
  - **FLOOR**: returns the nearest lowest number.
  ```sql
  SELECT FLOOR(12.45)
  -- outputs 12
  ```
  - **CEIL**: returns the nearest largest number.
  ```sql
  SELECT CEIL(12.45)
  -- outputs 13
  ```
  - **TRUNCATE**: removes the decimal places of the number.
  ```sql
  SELECT TRUNCATE(number, decimal_places_to_retained)
  SELECT TRUNCATE(12.45, 0)
  -- outputs 12
  ```
  - **ROUND**: returns the rounded number.
  ```sql
  SELECT ROUND(decimal, decimal_places_to_retained)
  SELECT ROUND(12.45678, 0)
  -- outputs 12
  ```
  - **MOD**: returns the remainder of the specified arguments.
  ```sql
  SELECT MOD(divident, divisor)
  SELECT MOD(10, 3)
  -- outputs 1
  ```
  - **SQRT**: returns the square root of a number.
  ```sql
  SELECT SQRT(16)
  -- outputs 4
  ```
  - **POWER**: raise the number to the power of another.
  ```sql
  SELECT POWER(base, exponent)
  SELECT POWER(2, 3) same as 2 x 2 x 2
  -- outputs 8
  ```
  - **RAND**: returns a floating point number between 0 and 1.
  ```sql
  SELECT RAND()
  -- outputs 0.0012323
  ```
- **String functions**:
  - **CONCAT**: merge all the specified string into 1 output.
  ```sql
  SELECT CONCAT(names...)
  SELECT('Hello', 'World')
  -- outputs Hello World
  ```
  - **SUBSTRING**:
  ```sql
  SELECT SUBSTRING(stack, start, end)
  SELECT SUBSTRING("Hello World", 2, 5)
  -- outputs ello 
  ```
  - **LENGTH**: returns the length pf the given string.
  ```sql
  SELECT LENGTH("Hello World")
  -- outputs 11
  ```
  - **UPPER**: converts string inyo uppercase characters.
  ```sql
  SELECT UPPER("hello world")
  -- outputs HELLO WORLD
  ```
  - **LOWER**: converts string into lowercase characters.
  ```sql
  SELECT LOWER("HELLO WORLD")
  -- outputs hello world
  ```
  - **TRIM**: removes leading and trailing whitespace.
  ```sql
  SELECT TRIM("   Hello World   ")
  - outputs Hello World
  ```
  - **REPLACE**:
  ```sql
  SELECT REPLACE(string, new_string, old_string)

  SELECT REPLACE("Hello World", "H", "W")
  -- outputs Wello World
  ```
  - **INSTR**: returns the index of given needle to the haystack
  ```sql
  SELECT INSTR(haystack, needle)
  SELECT INSTR("Hello", H)
  -- outputs 1
  ```
- **Date and Time functions**:
  - **NOW**:
  - **YEAR**:
  - **MONTH**:
  - **DAY**:
  - **HOUR**:
  - **MINUTE**:
  - **SECOND**:
  - ****:
  - ****:
  - ****:
- **Miscellaneous functions**:
  - **IFNULL and COALESCE functions**:
    - Returns the first non null value in the given argument else returns the specified value if all the arguments are null
    ```
    SELECT COALESCE(column_name1,            column_name2, default_value);
    ```
    - Here if column_name1 is NOT NULL  it returns the column_name1 value
    - if column_name1 is NULL then proceed to column_name2 if column_name2 is NOT NULL it returns the column_name2.
    - If both of the column_name1 and column_name2 is NULL it returns the default value.

    So basically in IFNULL the same logic is applied the difference is IFNULL only takes 1 arguments unlike COALESCE it takes multiples arguments before returning the default value.

## 5 Aggregate Function
- **SUM(column_name)**: Returns the sum of a given numeric column.  
- **AVG(column_name)**: Returns the average of given numeric column.  
- **MIN(column_name)**: Returns the minimum value of given column.  
- **MAX(column_name)**: Returns the maximum value of given column.  
- **COUNT(column_name)**: Returns the total record of given column.  

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
- DATE (YYYY-MM-DD)
- TIME (HH:MI:SS)
- DATETIME (YYYY-MM-DD HH:MI:SS)
- TIMESTAMP (YYYY-MM-DD HH:MI:SS)
- YEAR (YYYY)

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
- **GROUP BY**
  - Used to display data in groups
  - GROUP BY can only be used if the query uses AGGREGATE functions
  - When using it you saying like "Show us the count of orders, but group the count by each product"
  - Selected fields are usually used also in GROUP BY column
```
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
```
- **HAVING**
  - Is usually used after GROUP BY, it filters data but in groups
  - Usually used with AGGREGATE functions
```
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
HAVING SUM(another_column_name) > 1000;
```
- **ORDER BY**: Used to sort the returned rows via specified column with ascending as default.
```
SELECT column_name
FROM table_name
ORDER BY column_name
```
- **USING**: Used when the columns of joining tables are exactly the same.
```
SELECT *
FROM left_table
JOIN right_table ON left_table.record_id = right_table.record_id;
-- instead
SELECT *
FROM left_table
JOIN right_table USING (record_id);
```
- **CASE**: Just like switch in any other languange you should know this.
```
CASE
  WHEN expression THEN return_value
  WHEN expression THEN return_value      ELSE default_value
END
```
- **IF**: just like in any languange if you should know this. looks like a ternary operator.
```
IF(expression, true, false)
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
## Inner Join/ Join
- Returns only the matching records between to tables.
- This usually what we want in program
- The tables should have relationship the FK.
```
SELECT [column_names]
FROM table_name tn
INNER JOIN another_table_name atn ON tn.primary_key = atn.foreign_key
```

## Left Join/ Left Outer Join
- Returns the matching records and the non-matching records in the left table. Basically doing inner join to return the matching record then returns also the non-matching of the left table.
```
SELECT [column_names]
FROM left_table lt
LEFT JOIN right_table rt ON lt.primary_key = rt.foreign_key
```

## Right Join/ Right Outer Join
- Returns the matching records and the non-matching records in the right table. Basically doing inner join to return the matching record then returns also the non-matching of the right table.
```
SELECT [column_names]
FROM left table lt
RIGHT JOIN right_table rt ON lt.primary_key = rt.foreign_key
```

## Full Join/ Full Outer Join
- This is the result when three of the joins combined the inner join, left join, and the right join. Basically return the matching record and return the nonatching record for both the right and left table.
```
SELECT [column_names]
FROM table_name tn
FULL JOIN another_table_name atn ON tn.primary_key = atn.foreign_key
```

## Cross Join
- Return the cartesian product of the tables
- Dont need a join condition.
- For example left table has 6 records amd right table has 4 records what it will do is the every record in left table will be match to 4 records. so with that in mind the ouput will be 24 becuase 1 record of left table will be mapped to all 4 records in right table. its like 1:4 ratio.

## Compound Join
- When table is cannot be uniquely identified with single column usually a table thats not have primary key. instead it can be uniquely identified with 2 or more columns.
- The real world example for this is the employee, product, and order tables where each order record does not have primary key instead its uniquely identified based on given product and employee.

## Natural Join
- The database engine will join the tables based on common column_names existed in both tables. Its dangerous to use this because we are letting the database engine to guess the columns to join instead of use defining it because and this join are not recommended because it produces random results when database table columns name are modified.
```
SELECT *
FROM left_table
NATURAL JOIN right_table 
```

## Union Join
- Is used to combined result set of multiple queries.
- Basically it will merge all the result set of both queries
```sql
SELECT name
FROM employee
UNION
SELECT name
FROM product
```

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

# Parameter
## 2 types of parameter
- **IN**: Used to pass values into procedures and functions
Cannot be modified inside.
- **OUT**: Used to return values from prcedures and functions. Basically your return type will be initialize null and can be modified inside.

# Variable
## Session variables
- Prefixed with @
- Available only for 1 session or 1 run
No declaration needed.
- Created when you assign a value.
```
SET @age = 18
SELECT @age
```

# Local variables
- Created using DECLARE keyword
Only available/ scoped within the stored procedure, function, and trigger.
- Must be declared before using.
```
DECLARE variable_name data_type
or
DECLARE age INT
```

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

# How to connect to your local machine MySQL Server remotely
- First Make sure your local machine (Where your MySQL Server is installed) and your other device (The device that will connect in your local machine MySQL Server) is connected in the same wifi or network for them to communicate.
```sql
-- Step 1. Create user
-- Template:
CREATE USER '<username>'@'<allow-ip-address>' IDENTIFIED BY '<password>';

-- Where <username> is the username.
-- Where <allow-ip-address> is the ip addresses allowed to access the <username> user. To allow all the ip address to access that user we use '%'. Or you can specify specific ip address (The remote pc ip address) for more security concerns
-- Where <password> is the password

-- Example:
-- Specific IP Address
CREATE USER 'elleined'@'192.168.1.1'  IDENTIFIED BY 'elleined';

-- All IP Address
CREATE USER 'elleined'@'%'  IDENTIFIED BY 'elleined';

Step 2: Grant privileges to a user
-- Template:
GRANT ALL PRIVILEGES ON <database-name>.<table-name> TO '<username>'@'<allow-ip-address>';

-- WHERE <database-name> is the database that the specified <username> user allowed to access. Use * to allow all database to be accessed.
-- WHERE <table-name> is the table that the specified <username> user allowed to access within the specified <database-name>. Use * to allow all table to be accessed.
-- WHERE the <username> is the username you specify in step 1 in this case (elleined).
-- WHERE the <allow-ip-address> is the ip address you specify in step 1 in this case (192.168.1.1).

-- Example:
-- Granting specific database and table
GRANT ALL PRIVILEGES ON my_db.my_table TO 'elleined'@'192.168.1.1';

-- Granting all database and table
GRANT ALL PRIVILEGES ON *.* TO 'elleined'@'192.168.1.1';

-- Granting specific database and all tables
GRANT ALL PRIVILEGES ON my_db.* TO 'elleined'@'192.168.1.1';

Step 3: Apply the changes. !DONT FORGET THIS COMMAND OR ELSE ALL THE WORK YOU DO WILL NOT WORK!
FLUSH PRIVILEGES

Step 4: Allow remote connection in your MySQL Server
https://www.digitalocean.com/community/tutorials/how-to-allow-remote-access-to-mysql

Basically you will do is:
a. Change the bind-address = 0.0.0.0 to allow remote connections because by default mysql server only allow localhost which is 127.0.0.1

Step 5: Connect ot MySQL Server remotely
-- In your remote pc
-- Template:
-- Via CLI but you can use mysqlk= workbench instead
mysql -u <username> -p -h <server-ip-address>

-- Example:
mysql -u elleined -p -h 192.168.1.2
```

## Analogy
- So normally to access your MySQL Server in your local machine you user the localhost:3306 and you will access it using other device with 192.168.xxx.xxx:3306 where localhost is your local machine default IP of 127.0.0.1 meanwhile 192.168.xxx.xxx is the IPv4 of your local machine in internet. Thats why you need them to be in the same network for them to communicate so that your other device will communicate/ connect in your local machine IPv4 Address allowing other device to access your local machine MySQL Server. So don't be confuse with localhost and 192.168.xxx.xxx, localhost is your local machine private IP while 192.168.xxx.xxx is your local machine public IP.

# Cool commands
## Quickly copy a table
- It will copy all the data but not the table attributes
```
CREATE TABLE new_table_name AS
SELECT * FROM existing_table_name
```

## Insert a record in table with query
```
INSERT INTO target_table
SELECT * FROM source_table
```
