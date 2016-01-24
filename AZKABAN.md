# AZKABAN KNOWLEDGE

* Scheduler for running Hadoop tasks
* Has a web interface
* **Azkaban** consists of:
  * MySQL database
  * Azkaban web server
  * Azkaban executor server
  
###### Mysql:
* Azkaban stores its state in MySQL
* **AzkabanWebServer** uses:
  * Project Management //files, permissions, projects
  * **Flow state** keeps track of flows and which executor is running them
  * Previous **flows, jobs** stores prevous executions of jobs ant their log files
  * **Scheduler** keeps the state of the scheduled jobs
* **AzkabanExecutorServer** uses:
  * **Access to project** - gets files from db
  * Stores logs
  * etc
  
###### AzkabanWebServer

* Main manager

###### AzkabanExecutorServer

#### FLOWS
* Job is a process to be run in Azkaban
* Graph set up by several jobs and their dependancies makes up a flow
* **Flow** is a set of jobs, that depends on one another
* Job can only run after its dependencies


