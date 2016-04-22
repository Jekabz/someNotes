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
![pic]()
