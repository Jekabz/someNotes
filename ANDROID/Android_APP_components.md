#App components
* has multiple app entry points
* app is a cooperating group of components

####Activity, Intent, task
* `Activity` typically fills the screen and is also a unit of execution
* `Intent` is unit of communication, it allows one `Activity` to launch another
* each `Activity` is largely seperate from others
* keep no references to other `Activity` objects
* applications describe an `Intent` that they want to execute and ask the system to find one that matches
* `Task` is a chain of activities


----
* `services` supports background functions
* `ContentProvider` provides access to a data store form multiple apps
* `Broadcast Receiver` alows multiple parties to listen for `intents`

######Content Providers
* `ContentProvider` got methods:
  * Insert -- inserts new records in a database
  * Query -- return a set of records
  * Update -- replaces records in database with new ones
  * Delete -- removes matching records from a database
* `ContentProviders` manage entire SQL tables

######Broadcast Receiver
* recieves `intents`
* has no UI

####static app resources and context
* `Manifest` and `resources`

######App Manifest
* describes components of app
