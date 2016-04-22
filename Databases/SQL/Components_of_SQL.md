#Components_of_SQL
* `data definition language`
  * creates tha database
  * modifies database structure
  * destroys the database
* `data manipulation language`
  * performs database maintenance
  * enters, changes, removes data
* `data control language`
  * protects the database from becoming corrupted
  * provides security

----
####Data definition language
* create, change, destroy the elements of a relational database
* elements include
  * tables
  * views
  * schemas
  * catalogs
  * clusters
  * other stuff

* `tables` contain `rows` and `columns`
* `schemas` contain `tables` and `views`
* `catalogs` contain `schemas`
* __database contains catalogs__, it is sometimes referred to as a cluster

######Creating tables
* `CREATE TABLE`
* `ALTER TABLE`
* `DROP TABLE`

```sql
CREATE TABLE TableName (
  CustomerId  INTEGER  NOT NULL,
  FirstName   CHAR (15),
  LastName    CHAR (15) NOT NULL
);
```

* __VIEW__
  * Has no independent physical existance
  * a virtual table
  * views data is not physically duplicated in memory
  * __single table view:__
    * derived from a single table
    ```sql
    CREATE VIEW Foo AS
    SELECT TableName.FirstName,
    FROM TableName
    WHERE TableName.LastName = 'something';
    ```
    or:
    ```sql
    CREATE VIEW Foo AS
    SELECT FirstName
    FROM TableName
    WHERE LastName = 'something';
    ```
  * __multitable view
    * pulls data from multiple tables
    ```sql
    CREATE VIEW View AS
    SELECT Something,
           SomethingElse,
           SomeMoreThing
    FROM FirstTable JOIN SecondTable
    USING (ColumnName);
    ```

####Collecting tables into logical schemas
* `logical schema` -- organizational structure of a collection of related tables
* each project gots its own schema (its like a namespace, or package, because schemas can have tables with the same name)
* there is also a default schema

####Ordering by catalog
* `catalog` goes above schemas to avoid identical schema names for large databases
* you can refer to a table by:
`CATALOG_NAME.SCHEMA_NAME.TABLE_NAME`
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-22%2014:45:33.png)
* At the very top of the heirarchy are `clusters`
* the catalog is most commonly used top level
* catalog also contains `information schema`
* `information schema` contains system tables, that hold metadata for other tables
  * maketh the database self - describing this way

----
####Data Definition language Statements
* `CREATE` -- *builds essential structures of the database*
* `ALTER` -- *changes already existing structures*
* `DROP` -- *destroys structures*

######CREATE
* schemas, domains, tables, views existance
* creating schema allows you to identify its owner and default charset:
```sql
CREATE SCHEMA foo
AUTHORIZATION Prezident
DEFAULT CHARACTER SET ASCII_FULL ;
```
* `create domain`  applies Constraints to columnn values, you can do this after defining a schema:
```sql
CREATE DOMAIN Age AS INTEGER
CHECK (AGE>20);
```
* `CREATE ASSERTION` will specify Constraints that applies to entire schema

######ALTER
* Change by adding, deleting or modifieing a column in a table
* you can also `ALTER` columns or domains

######DROP
* Drop erases all data in a table, as well as metadata that defines the table
* Drop will not work if it breaks the __referential integrity

----
####Data Manipulation Language
* Handles data itself
  * `INSERT`
  * `UPDATE`
  * `DELETE`
  * `MERGE`
  * `SELECT`
#####Value expressions
* combines 2 or more values:
  * Numeric
  * String
  * Datetime
  * Interval
  * Boolean
  * User Defined
  * Row
  * Collection
######Numeric value expressions
`*, -, +, - `
```sql
:MONTH/12
```
`:` mens that it is a parameter or a host variable

######String value expressions
* `||` or `+` - concatenation
* Works on text or binary strings

######Datetime and interval value expressions
* `interval value` expressions deal with diff in between one datetime and another
* you gots:
  * `year month` interval
  * `day time` interval

######Boolean value expressions
* true or false of a predicate
`(Class = SENIOR) IS TRUE`
`NOT (Class = SENIOR) IS TRUE`
`(Class = SENIOR) IS FALSE`
`(Class = SENIOR) IS UNKNOWN`

######User defined type expressions
* expressions that gots data elements od UDT, must return UDT aswell

######Row value expressions
`(‘Joseph Tykociner’, ‘Professor Emeritus’, 1918)`

######Collection value expressions
* evaluates to an arr

######Reference value expressions
* evaluates to a value that references to some other db component, such as table

####Predicates
* comparisons:
  *`=` -- equals
  * `<>` -- not equals
  * `<`
  * `>`
  * `<=`
  * `>=`

######Logical connectives
`Class = SENIOR AND Age < 14`
`NOT (Class = SENIOR)`

######Set functions
* when info you need is in an aggregate of table rows
  * `COUNT`
    * returns a number of rows in a specified table
    ```sql
SELECT COUNT (*)
FROM STUDENT
WHERE Grade = 12 AND Age <14 ;
    ```
  * `MAX`
    * return the max value in a column
    ```sql
SELECT FirstName, LastName, Age
FROM STUDENT
WHERE Age = (SELECT MAX(Age) FROM STUDENT);
    ```
  * `MIN`
    * same as `MAX` but for min val
  * `SUM`
    * adds up the values in a specified column (Numeric type column)
    `SELECT SUM(foo) FROM bar;`
  * `AVG`
    * returns average of all values in a specified column
    * applies only to columns with a numeric data type
    `SELECT AVG(foo) FROM bar;`
    * __null__ has no value and are ignored in `AVG`

######Subqueries
* Querieception
* Anywhere you can use as expression or a SQL statement, you can also use a Subquerie

----
####Data Control Language
* protects DB FROM HARM
  * `COMMIT`
  * `ROLLBACK`
  * `GRANT`
  * `REVOKE`

######TRANSACTION
* making changes are dangerous to a db, because while change happens, a software or hardware error can happen
* sql protects db by allowing any change to happen only within `transaction`
* if failure occurs, you can get to the database state before starting the `transaction` by issuing `ROLLBACK` statement
* `transaction` writes what it is doing in a log file
* `ROLLBACK` goes through this log in reverse and undoes actions
* when db is used by multiple users, each of their actions happens in an individual `transaction`

######Users and privileges
* users are a danger to data integrity
* users need to be classified and priviledges gots to have categories
* he ho maketh schema, also has it upon himself to name the __owner__
* he ho is __owner__, can grant access priviledges to users, any priviledges not specified are witheld
* SQL giveth capability to protect these objects:
  * tables
  * columns
  * views
  * domains
  * character sets
  * collations
  * translations

* SQL giveth different kinds of __protection__
  * seeing
  * adding
  * modifying
  * deleting
  * referencing
  * using
* You permit access by using the `GRANT` statement
* You revoke access by using tha `REVOKE` statement
```sql
GRAND SELECT ON Foobar TO whoever;
```

####Referential integrity Constraints
* `referential integrity` is a property af a db, when data in one table is consistent with data in all other tables
* to ensure referential integrity`, database designers apply constraints to tables that restricts data that users can enter into tables

* dont do this:
```sql
GRANT ALL PRIVILEGES
ON FOUR_STAR
TO Benedict_Arnold WITH GRANT OPTION;
```
