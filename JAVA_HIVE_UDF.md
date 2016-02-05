#JAVA HIVE UDFs

* There are 2 interfaces to do this:
  * `org.apache.hadoop.hive.ql.exec.UDF` -- *the simple API for **primitive** data types*
  * `org.apache.hadoop.hive.ql.udf.generic.GenericUDF` -- *the more complex API for **complex** data types*

------------------------
#### THE COMPLEX API

* `org.apache.hadoop.hive.ql.udf.generic.GenericUDF` requires to implement 3 methods:
  * `abstract Object evaluate(GenericUDF.DeferredObject[] arguments);` -- *takes args, returns _boolean_ result*
  * `abstract String getDisplayString(String[] children);` -- *returns some string, does not matter*
  * `abstract ObjectInspector initialize(ObjectInspector[] arguments);` -- *used for input validation _passes data to UDF_*
 
