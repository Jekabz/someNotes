# SQL

#### DATABASE BASICS

* Data stored in the table is one type of data or one list, if need more, just create several tables
* Table names are unique
* `Schema` -- Information about database and table layout and properties.
* `Primary key` -- column that uniquely identifies every table row
  * Primary key must be unique
  * Does not allow `null`
  * Primary key value should never be modified
  * Primary key values should never be reused. (If a row is deleted from the table, its primary key may not be assigned to any new rows in the future.)
  * Multiple columns may be used together as a primary key

----
#### SQL
* SQL statements are case insensitive

###### Select statement
* by default, returns data without significant order
```SQL
SELECT DISTINCT --DISTINCT will only return unique values in all columns
columnname1, columnname2, columnnameN
FROM Tablename
WHERE columnname1 operator value
ORDER BY columnnamex ASC, columnnamey DESC -- you can also sort data by the column that is not selected and by multiple columns, sort sequence is as specified, first column first, followed by others. You can substitute columnname by collumnposition in select list (number)
LIMIT 5 -- return no more than 5 rows
OFFSET 5 -- last row still to be excluded. No offset is possible without limit
; -- ends with semicolin!
```
###### Comments
```SQL
-- comment
# comment
/*
multiline
comment
*/
```
###### Sorting data
###### Filtering data
* operators for `WHERE`:
![pic]()
