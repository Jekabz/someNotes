#Activities

######Activity
* Single screen with an UI. that user interacts with
* Screen can take up all the display, or part of it, or it can float
* if app gots more activties, one should be marked as "main"
* app usually got several Activities
* each time a new activity starts, the previous one is stopped, but preserved in "back stack"
* "back stack" -- last in, first out

----
![pic](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-16%2019:48:00.png)

* callback == event

####Creating an Activity
* you extend an `Activity` class
* in your subclass, implement callback methods (called by system)

* `onCreate()`
  * initialize most important components of your Activity
  * call `setContentView()` to define the layout for UI
* `onPause()`
  * means that the user might not come back, so you should save changes that should go beyond the current session

####Implementing the UI
* UI for the activity is composed of views
* Each view is a rectangle on display, that can respond to user interaction, like a button

####Declaring the activity in the Manifest
* activity has to be declared in the Manifest, or it will not be accessible
```xml
<manifest ... >
  <application ... >
      <activity android:name=".ExampleActivity" />
      ...
  </application ... >
  ...
</manifest >
```
######Using intent filters
* You should have one `main` activity:
```xml
<activity android:name=".ExampleActivity" android:icon="@drawable/app_icon">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```
* if other apps should not activate your app's activities, you dont need any other intent filters

######Starting an activitty
* You start an activity by calling `startActivity()`, that will pass an `Intent`
* `Intent` can also contain small amount of data
```Java
Intent intent = new Intent(this, SignInActivity.class);
startActivity(intent);
```
* You can also call activities from other apps
```Java
Intent intent = new Intent(Intent.ACTION_SEND);
intent.putExtra(Intent.EXTRA_EMAIL, recipientArray);
startActivity(intent);
```

######Starting an activity for a result
* Sometimes, you start an activity to get some result from it
* You do this by `startActivityForResult()` instead of `startActivity()`
* In the caller, implement the `onActivityResult()` method, that will receive the result from an `Intent`

######Shutting Down an Activity
* call the `finish()` method
* you dont really need to do this as activity lifecycle is managed by the Android OS

######Managing the Activity lifecycle
