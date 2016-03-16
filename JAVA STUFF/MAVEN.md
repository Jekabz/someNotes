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
* `mvn package` -- *does __mvn compile__ runs tests, in target directory, makes \<\<artifactId\>\<version\>\>.jar files*
* `mvn install` -- *does __mvn compile__ and copies the jar from my project into local maven dependency repo, ready for another project to refer to*

------------------------------
#### DEPENDENCY MANAGEMENT

```xml
    <dependencies>
        <dependency>
            <groupId>The group or organization that the dependency belongs to</groupId>
            <artifactId>The library that is required</artifactId>
            <version>The specific version of the library that is required</version>
            <scope>See below</scope>
        </dependency>
    </dependencies>
```
* `<scope>` see the choices below:
  * `compile` -- *default option, dependency should be available at compile time*
  * `provided` -- *Dependencies that are required for compiling the project code, but that will be provided at runtime by a container running the code (e.g., the Java Servlet API).*
  * `test` -- *Dependencies that are used for compiling and running tests, but not required for building or running the project’s runtime code.*

----------------------------
## MAVEN PLUGINS

----------------------------

#### MAVEN SHADE PLUGIN

* Makes an __Uber Jar__ - a .jar that contains everything - all the dependencies
* Normally (without Maven Shade), the .jar contains only the classes/resources to itself
* __Uber Jar__ takes dependencies, extracts them in project classes
* __Uber Jar__ is all that is needed for code deployment
* Do not put __Uber Jar__ in Maven dependency, it will ruin the dependency resolution 
