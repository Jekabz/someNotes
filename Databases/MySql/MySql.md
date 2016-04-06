# MySQL

* Database has one or more tables

###### Data types
* __CHAR__ data type:
  * `VARCHAR(int)` --*VARiable length CHARacter string. int is max length allowed. longer values will be truncated. VARCHAR is slower than CHAR.*
  * `CHAR(int)` --*CHARacter string with max int length. Shorter input will be added spaces until max is reached. CHAR is faster than VARCHAR.*
  ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-05%2001:27:25.png)
* __BINARY__ data type:
  * Stores strings of full bytes that do not have an associated char set. (you can store a file like this)
  ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-05%2001:27:36.png)
*  __TEXT__ data type:
  * VARCHAR is faster for searches than TEXT
  ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-05%2001:27:50.png)
* __BLOB__ data type:
  * Binary Large OBject
  * Use for large binary data
  * BLOB cannot have default values
  ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-05%2001:28:03.png)
* __NUMERIC__ data type:
  * To specify signed or unsigned, use `UNSIGNED`:
    `INT UNSIGNED`
  ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-05%2001:28:18.png)
* __DATE__ and __TIME__:
  * `TIMESTAMP` holds valuse from 1970 - 2037, `DATETIME` holds just about everything
  ![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-05%2001:28:29.png)
* __AUTO_INCREMENT__ data type:
  * Causes MySQL to set a unique valu for this column in every row

###### Adding data to a table
`INSERT INTO tableName(column1, coulmn2)VALUES('val', 'val');`

###### Rename a table
`ALTER TABLE nameOld RENAME nameNew;`

###### Change column data type
`ALTER TABLE tableName MODIFY columnName NEWTYPE;`

###### Add a new column
`ALTER TABLE tableName ADD newColumnName NEWTYPE;`

###### Rename a column
`ALTER TABLE tableName CHANGE columnOldName columnNewName TYPE; `

###### Removing a column
`ALTER TABLE tableName DROP coolumnName;`

###### Remove table
`DROP TABLE tableName`

----
#### INDEXES
* improves search speed and querie performance a __lot__

###### Create an index
* Different INDEX types are:
  * INDEX
  * PRIMARY KEY
  * FULLTEXT
`ALTER TABLE tableName ADD INDEX(columnName(int firstNCharsToBeIndexed));` -- integers do not need limit
