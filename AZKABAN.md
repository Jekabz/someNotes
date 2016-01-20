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
