#Using SQL to build databases

####INDEX
* used for a fast access
* `index` is a table of pointers
* each row in `index` points to a corresponding row in the data table
* you can define an index for all the different ways you may want to access your data
* if you change rows in data table, you only need to update the indexes
* `PRIMARY KEY` of any table should always be indexed

* index fields you frequently use to access rows
* index fields that have differentiation between rows
* `INDEX` is not a part of SQL, and is DBMS specific
* Depending on DBMS, `DROP INDEX` might also be possible

----
```SQL
CREATE TABLE Foo(
  Something     INTEGER      PRIMARY KEY,
  SomethingElse VARCHAR(10)
);

ALTER TABLE Foo(
  ADD COLUMN SomethingFoo VARCHAR(10);
  DROP COLUMN SomehtingElse;
);
```
