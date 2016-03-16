# MAVEN

#### MAVEN ASSEMBLY PLUGIN

* Aggregates project output with dependancies, modules, docs etc into a single dizstributable archive.
* There are `descriptors` available to package project's artifacts into different formats

--------------------------
#### POM

* `<modelVersion` -- *Pom model version, usually 4.0.0*
* `<groupId>` -- *Group or organisation the project belongs to, often presented as inverted domain name*
* `<artifactId>` -- *This is name to be given to the projects library artifact*
* `<version>` -- *Version of the project that is being built*
* `<packaging>` -- *How the project should be packaged*

-----------------------------
#### MAVEN LIFECYCLE GOALS

* `mvn compile` -- *compildes into each .java file in .class file and places .class files in target directory*
* `mvn package` -- *does __mvn compile__ runs tests, in target directory, makes <artifactId><version>.jar files*
* `mvn install` -- **
