# SQL Notes #

## Database & Query ##
* Database - Database is a way of storing data in a format which makes it easily accessible
* Query - a command to the database to perform a task with syntax (like asking a question from database)
* CRUD - Create, Read, Update, Delete
* DBMS - Database Management System. we give query to DBMS and further it gives query to Database to perform CRUD.

## Relational vs Non-relational ##
* Relational --> 

## Tables ##
* Table is created using CREATE TABLE table_name(table_schema);
* Datatypes --> <br />
    1. INT - used for integer
    2. VARCHAR(100) - used for variable-length string and 100 is the length(it can vary)
    3. DATE - stores date value
    4. TIMESTAMP - stores date and time, automatically stores the current timestamp when a row is created
    5. ENUM - a string object with a value chosen from a list of permitted values
    6. BOOLEAN - stores TRUE or FALSE values
* Constraints -->
    1. AUTO_INCREMENT - automatically generates a new no for each row
    2. PRIMARY KEY - uniquely identifies a row in a table
    3. NOT NULL - a column cannot have NULL value
    4. UNIQUE - ensures all values are unique in a column
    5. DEFAULT - sets a default value if no value is provided

## Basic Query ##
* Selection - SELECT (column1, column2)/*(for everything) FROM table_name;
* Rename - RENAME TABLE table1 TO table2;
* Alter - ALTER TABLE table_name ADD/DROP (full-details of what you want to do with data types and constraints in case of ADD. and in case of DROP just put column_name);
* Modify - ALTER TABLE table_name MODIFY COLUMN column_name property-to-modify(eg- VARCHAR(150));
* Moving columns - ALTER TABLE table_name MODIFY COLUMN column_name_with_datatype AFTER another_column;

## Value Insertion ##
* Syntax - INSERT INTO table_name VALUES <br />
  (1, 'Alice', 'alice@google.com', 'male', '2004-02-02', ...); <br />
  Also we can use <br />
  INSERT INTO table_name (we can specify the column name that we are inserting value for) VALUES

## Terminology ##
* WHERE - conditional query
* AND / OR - combine conditions
* ORDER BY - orders the rows (DESC - descending, ASC - ascending)
* LIMIT - no of rows needed in output
* OFFSET - no of rows to skip before giving output