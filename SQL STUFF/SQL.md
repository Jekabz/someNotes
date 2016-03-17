# SQL

### DATABASE BASICS

* Data stored in the table is one type of data or one list, if need more, just create several tables
* Table names are unique
* `Schema` -- Information about database and table layout and properties.
* `Primary key` -- column that uniquely identifies every table row
  * Primary key must be unique
  * Does not allow `null`
  * Primary key value should never be modified
  * Primary key values should never be reused. (If a row is deleted from the table, its primary key may not be assigned to any new rows in the future.)
  * Multiple columns may be used together as a primary key
