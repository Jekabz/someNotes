#JAVA HIVE UDFs

* There are 2 interfaces to do this:
  * `org.apache.hadoop.hive.ql.exec.UDF` -- *the simple API for __primitive__ data types*
  * `org.apache.hadoop.hive.ql.udf.generic.GenericUDF` -- *the more complex API for __complex__ data types*

------------------------
#### THE COMPLEX API

* `org.apache.hadoop.hive.ql.udf.generic.GenericUDF` requires to implement 3 methods:
  * `abstract Object evaluate(GenericUDF.DeferredObject[] arguments);` -- *takes args, returns __boolean__ result*
  * `abstract String getDisplayString(String[] children);` -- *returns some string, does not matter*
  * `abstract ObjectInspector initialize(ObjectInspector[] arguments);` -- *used for input validation __passes data to UDF__*
 
