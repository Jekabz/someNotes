# SPARK KNOWLEDGE

######OVERALL:
* First tihing in every spark programm is to make sparkContext object, which tells spark how to access a cluster, in Scala, this is sc variable, created automatically
* Spark context is used, to create other variables
* scala>sc
  res: spark.SparkContext = spark.SparkContext@something

###### MASTER:
* master parameter for sc determines, which cluster to use: local[x] -- `x use worker threads`
* connects to cluster manager, to allocate resources across apps
* acquires executors on cluster nodes //executors run processes and stores data
* sends app code to executors
* sends tasks for executors to run

#########################  RDD  #########################################
* RDDs can only be created through deterministic operations on data or other RDDs
* fault tolerant collection of elements, that can be oprated on in parallel
* There are 2 types of RDD:
   1) parallellized collections, that take Scala collection and runs functions on it in parallel
   2) Hadoop datasets - in hdfs, run functions on each file record
* There are two kinds of operations on RDD:
   1) transformations (lazy #not computed immediately)
   2) action (not lazy)
* RDD is recopmuted, when action is run on it
scala> val data = Arr(1, 2, 3)
scala> val distData = sc.parallelize(data)
* Spark can create RDDs from any file in hdfs or other hdfs supported storages
scala> val distFIle = sc.textFile("foo.txt")

##########################  TRANSFORMATIONS  ############################
* Transformations create a new dataset from existing one
* All transformations are lazy, but Scala collections are strict
* There are many trasnformations:
	map(func)	
	filter(func)
	flatMap(func)
	sample(withReplacement), fraction, seed)
	union(otherDataset) #returns new dataset uniting the elements in source dataset
	distinct([numTasks]) 
	groupByKey ([numtasks])
	reduceByKey (func, [numTasks])
	sortByKey ([ascending], [numTasks])
	join (otherDataset, [numTasks])
	cogroup (otherDataset, [numTasks])
	cartesian (otherDataset)
scala> val distFIle = sc.textFile("foo.txt") #collection of lines,
# if you want to take file from local filesystem, do: sc.textFile("file:////path") 
scala> distFile.map(l => l.split(" ")).collect()
##########################  ACTIONS  ####################################
	reduce (func)
	collect() #returns all elem of dataset as arr, used after a command that returns small subset of data
	count()
	first()
	take(n) #returns arr with the first n elements of the dataset
	takeSample (withReplacement, fraction, seed)
	saveAsTextFile(path) #Spark will call toStrig on each element
	saveAsSequenceFile(path) #Only awailable on RDDs of key walue pairs, that can be converted to Hadoops writable interface
	countByKey() #Only for RDDs of type (k, v), returns Map(k, int)
	foreach(func) #Run func on every element in dataset
scala> val f = sc.textFile("foo.txt")
scala> val words = f.flatMap(l => l.split(" ")).map(word => (word, 1))
scala> words.reduceByKey(_+_).collect.foreach(println)

##########################  PERSISTANCE  #################################
* Spark can can cache dataset in memory across operations
* Node stores slices of datasets that it works on, for future reuse
* Cache is fault tolerant, if part of RDD is lost, it will be recomputed using trasnformations, that originally created it
* Tere are several persistance modes:
	MEMORY_ONLY #Stores RDD as deserialized Java objects in JVM, if RDD does not fit, parts will not be cached, this is default mode
	MEMORY_AND_DISK #Same as MEMORY_ONLY, but ir parts of RDD do not fit, they will be stored on disk
	MEMORY_ONLY_SER #RDDs stored as serialized Java objects. More cpu intensive, more space efficient
	MEMORY_AND_DISK_SER #Similar to MEMORY_ONLY_SER, but, if partitions do not fit on disc, they will be stored on disc
	DISK_ONLY # Stores RDDs on disk
	MEMORY_ONLY_2, #Same as MEMORY_ONLY, but replicates each partition on two cluster nodes
	MEMORY_AND_DISC_2 #Same deal

############################  BROADCAST VARIABLES  #######################
* Broadcast var is read only var cached on each machine, not shipped in with tasks
* Could give each node a copy of large dataset efficiently
* To reduce communication cost, B V are distributed in with special algorithms
scala> val broadcastVal = sc.broadcast(Array(1, 2, 3))
scala> broadcastVar.value
############################  ACCUMULATORS  ##############################
* Accumulators are variables, that can only be changed with associative (+, -, etc) operation
* Accumulators efficiently implement in parallel counters and sums
* Only the driver programm can read accumulator value, not the tasks
scala> val acc = sc.accumulator(0)
scala> sc.parallelize(Array(1, 2, 3)).foreach(x => acc +=x)
scala> accum.value
############################ (K,V) PAIRS #################################
scala> val pair = (a, b)
scala> pair._1 //=>a
scala> pair._2 //=>b

############################  SPARK SQL  #################################

############################  SPARK STREAMING  ###########################
* Extends core API to allow high throughput, fault tolerant sream processing on live datastreams
* Ingests from Kafka, Flume, etc.







