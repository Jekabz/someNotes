# ECLIPSE

#### Open up an existing (non eclipse) java project from source folder:

* file/new/java_project
* give project a name
* uncehck [ ] `use default location`
* add .gitignore
* choose directory with non eclipse project
* press `next`
* add project <projectname> to build path # Maybe not?
* press `finish`
* configure the build path with necessary jars if needed
* resolve errors, if any

---------------------------


#### Run maven:

* To run maven first JDS needs to be added to eclipse:
  * got to window/preferences/java/installed JREs/execution environments, click on java version and tick appropiate jdk version on right pane
  * if no jdk is shown on left pane, go to window/preferences/java/installed JREs and click `add`, then browse to jdk folder in filesystem

* if not maven project, press configure/convert to maven project
* to fire off maven project, go to run as/maven `clean install` in goals
* to fire off maven with -e switch, add `<yourgoal> -e` in goals
