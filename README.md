# SQL Notes (Using MySQL) #

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
* Constraints --> Used to apply rules on columns to maintain accuracy, validity and integrity of data
    1. AUTO_INCREMENT - automatically generates a new no for each row. we can change the starting value using (ALTER TABLE table_name AUTO_INCREMENT = starting_value;) but the condition must be starting_value > MAX(value);
    2. PRIMARY KEY - uniquely identifies a row in a table. One per table and it's NOT NULL and UNIQUE by default <br />
        NOTE - it can be dropped but it is more restricted. it may fail if it is being used elsewhere like in a foreign key or auto_increment column.
    3. NOT NULL - a column cannot have NULL value
    4. UNIQUE - ensures all values are unique in a column
    5. DEFAULT - sets a default value if no value is provided

    ### PRIMARY KEY vs UNIQUE ###
    a table can have only one primary key but multiple unique constraints. <br />
    PRIMARY KEY dropping is more restricted but UNIQUE columns can be dropped easily

## Basic Query ##
* Selection - SELECT (column1, column2)/*(for everything) FROM table_name;
* Rename - RENAME TABLE table1 TO table2;
* Alter - ALTER TABLE table_name ADD/DROP (full-details of what you want to do with data types and constraints in case of ADD. and in case of DROP just put column_name);
* Modify - ALTER TABLE table_name MODIFY column_name property-to-modify(eg- VARCHAR(150)); <br />
  NOTE - Modify needs full column definition which means we need to write the whole column description. It always requires Data Types. MODIFY changes a column definition completely so we need to write everything we want in a column definition if we are using MODIFY.
* Moving columns - ALTER TABLE table_name MODIFY COLUMN column_name_with_datatype AFTER another_column;
* ADD CONSTRAINT/DROP CONSTRAINT - for ADD CONSTRAINT we have to use a constraint name. and for DROP CONSTRAINT we just have to put that constraint name. (ALTER TABLE users ADD CONSTRAINT uq_email UNIQUE (email);)

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
* UPDATE - to update any value (recommended to use WHERE to put a condition or it will change everything in the database/table) <br />
  syntax - UPDATE table_name SET (used to set the value you want) column_name = value (can update many columns but on that specific condition of WHERE) WHERE id = someId (it's used to update based on condition not all data in a specific column);
* DELETE - delete some data based on condition (DELETE FROM table_name WHERE any_condition) <br />
  NOTE :- always use WHERE unless and until you intentionally wants to delete everything and before deletion always use SELECT to check what will be affected

## Functions ##
--> functions helps to analyze, transform and summarize the data
* COUNT(*) - returns total count of row.
* MIN(col_name) / MAX(col_name) - returns min and max value of the data
* AS - used to give a temporary name(alias) to a column or table in a query result.
* SUM(col_name) / AVG(col_name) - returns total and average of the data
* IF() -- conditions functions <br />
  syntax - IF(condition, true_value, false_value) <br />
  NOTE - we can use CASE in place of IF() as well

## Auto Commit and Transaction ##
--> MySQL treats every query as a transaction and auto commits every query. <br />
--> we can turn this off using - SET autocommit = 0; <br />
--> this prevents auto commits and auto savings every changes until we specifically commits it using COMMIT; this is helpful in case of accidental deletion of wrong data. we can just rollback to the previous point using ROLLBACK; <br />
--> alternatively we can set some query under transaction without turning off autocommit and in that case also we can rollback to previous safe point that is the last COMMIT;.

## Foreign Keys ##
--> it's a column that creates a link between two tables. the value must match in both the table. helps to maintain data integrity between related tables