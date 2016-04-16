#ANDROID

####Architecture

######Linux kernel
* Has drivers for camera, display etc.
* memory management

######Libraries
* C/C++ Libraries
* Android Libraries, based on Java

######Android Runtime
* Dalvik Virtual Machine - a kind of JVM
* DVM runs each app in its own process, with its own instance of DVM
* Has some Libraries too

######Application Framework
* Java classes (API):
  * Activity Manager
  * Content Providers
  * Resource Manager
  * Notifications Manager
  * View System
* Use these APIs to control your app

######Applications
* Apps go to this layer

----
#### Application Components
* Applications Components are the building blocks for an Android app

######Activity
* Single screen with an UI. that user interacts with
* Screen can take up all the display, or part of it, or it can float
* if app gots more activties, one should be marked as "main"
* app usually got several Activities
* each time a new activity starts, the previous one is stopped, but preserved in "back stack"
* "back stack" -- last in, first out

######Service
* a component that runs in the background to perform long - running operations
* has no UI
* App can start a service, and it will run, even if user switches to another App
* Runs in `main` thread of its hosting process
* Two kind of services:
  * `Started`
    * invoked with `startService()` and runs in bg indefinately, even if component that started it, is destroyed. When task is done, service should stop itself. It does not return anything to the caller.
  * `Bound`
    * components interact with it, by sending requests and geting results
    * runs as long as any otyher app component is bound to it
    * multiple app components can bind to the service at once

######Broadcast Receivers
* respond to Broadcast messages from other apps or from the System
* initiates some Application

######Content Providers
* provides data from one app to another upon requests

######Manifest File
* All components must be declared in manifest.xml
* Manifest file is like an interface between app and Android OS

######Strings File
* Strings.xml contains all the text app uses

######The R File
* Brings together Java files with resources like strings.xml

######The Layout File
* Determines the look of an Activity on screen

######Other components
*`Fragment` -- portion of UI in an Activity
* `View` -- UI elements that is drawn on screen
* `Layout` -- View hierarchy that control the appearance on screen
* `Intent` -- Messages wiring components together
* `Resources` -- External elements like strings and pics
* `Manifest` -- Configs for the app

----
####Resource organization in Android Studio
