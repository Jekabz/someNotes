#INtents and intent filters
* `Intent` is a messaging object used to request an action from another `app component`
* __use cases__:
  * __to start an activity__
    * you start a new instance of `activity` by passing an `intent` to `startActivity()`
    * Intent describes the activity and may have some necessary data
    * if you want to recieve a result from the activity, call `startActivityForResult()`, the result will be delivered with another `Intent` to the caller `activity's` `onActivityResult()`
  * __to start a service__
    * for one time action, pass `Intent` to `startService()`
    * if the service gots clietn-server interface, pass your `Intent` to `bindService()`
  * __to deliver a broadcast__
    * `broadcast` is a message that any app can recieve
    * You deliver a `broadcast` to other apps by passing `Intent` to:
      * `sendBroadcast()`
      * `sendOrderedBroadcast()`
      * `sendStickyBroadcast()`

----
####Intent types
* __Explicit intent:__
  * specifies the component to start by its fully qualified class name
  * you use this to start a component in your own app, cuz you know the fully qualified class name
  * system starts the app component immediately
* __Implicit intent:__
  * does not specify the specific component
  * declares general action to perform
  * system finds the component to start by comparing `intent filters` in manifest of other apps in device
  * if multiple mach, system gives user a dialog

----
* `intent filter` -- expression in manifest that declares, what intents a component recieves
* if no `intent filter` is declared for activity, it can only be started by `Explicit intent`
* use `explicit intents`, because `Implicit intent` is a security hazard, cuz you dont know what service will respond

----
####Building an intent
`Intent` gots info that system uses to to determine which component to start, and it also gots info for that component
* info in `Intent`:
  * __Component name__:
    * name of the component to start
    * optional, but maketh the intent __explicit__
  * __Action__:
    * selects generic action to perform
    * you can specify your own actions
    * Common actions for starting an activity:
      * `ACTION_VIEW`
        * use, when activity gots some info to show to user
      * `ACTION_SEND`
        * when user wants to share info through another app
    * you can specify the __action__ with `setAction()` or `Intent` constructor
  * __Data__:
    * contains a link to a resource, type of which is dectated by intents action
  * __Category__:
    * string with additional info about the type of component that should handle this intent
    * intent can have any number of categories
    * most intents need no Category
    * common categories are:
     * `CATEGORY_BROWSABLE`
       * Something with displaying data referenced by a weblink
     * `CATEGORY_LAUNCHER`
       * similar to a main() function in oop
  * __Extras__:
    * key value pairs
    * carry additional info
    * add extras with `putExtra(keyname keyvalue)`
    * you can also make `Bundle` with extra data and insert that in an intent with `putExtra(bundle)`
    * there are many predefined extra keys
  * __Flags__:
    * works as metadata for `Intent`
    * flags may instruct the system how to launch an `activity`

----
####Example explicit intent
constructor:
`Intent(Context, Class)`
```java
Intent downloadIntent = new Intent(this, DownloadService.class);
downloadIntent.setData(Uri.parse(fileUrl)); // fileUrl is string, like web adress
startService(downloadIntent);
```

####Example implicit intent
* user might not have any apps, to handle the implicit intent, if this happens, app will crash, to avoid this, use `resolveActivity()` on `Intent`. non null means there is one or more apps that can take the `Intent`
```java
// Create the text message with a string
Intent sendIntent = new Intent();
sendIntent.setAction(Intent.ACTION_SEND);
sendIntent.putExtra(Intent.EXTRA_TEXT, textMessage);
sendIntent.setType("text/plain");

// Verify that the intent will resolve to an activity
if (sendIntent.resolveActivity(getPackageManager()) != null) {
    startActivity(sendIntent);
}
```
* if multiple apps can handle the `Intent`, you got to choose
######Forcing an app chooser:
* Do this when user might want to use different app each time (No option for default app)
```java
Intent sendIntent = new Intent(Intent.ACTION_SEND);
...

// Always use string resources for UI text.
// This says something like "Share this photo with"
String title = getResources().getString(R.string.chooser_title);
// Create intent to show the chooser dialog
Intent chooser = Intent.createChooser(sendIntent, title);

// Verify the original intent will resolve to at least one activity
if (sendIntent.resolveActivity(getPackageManager()) != null) {
    startActivity(chooser);
}
```

####Receiving an implicit intent
* in __manifest__, declare one or more `<intent-filter>` elements
* __explicit__ intent passes all the intent filters, it dont care
* in `<intent-filter>`, u specify one or more of these:
  * `<action>` declares intent action accepted
  * `<data>` type of data accepted
  * `<category>` intent category accepted, but you want this to be `CATEGORY_DEFAULT` by default
* you can have multiple intent-filters
* to really call your apps activity, use __explicit intent__
* `<intent-filters>` are not secure, because explicit intent bypasses them. Restrict access by setting `Exported` to false

```xml
<activity android:name="MainActivity">
    <!-- This activity is the main entry, should appear in app launcher -->
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>

<activity android:name="ShareActivity">
    <!-- This activity handles "SEND" actions with text data -->
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="text/plain"/>
    </intent-filter>
    <!-- This activity also handles "SEND" and "SEND_MULTIPLE" with media data -->
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <action android:name="android.intent.action.SEND_MULTIPLE"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="application/vnd.google.panorama360+jpg"/>
        <data android:mimeType="image/*"/>
        <data android:mimeType="video/*"/>
    </intent-filter>
</activity>
```
######Using a Pending Intent
* `PendingIntent` is a wrapper around an `Intent` object
* use to grand permission to use the contained `Intent` like it was executed from apps own process
* Use cases:
  * Executes `Intent` when user clicks on Notification
  * Executes `intent` when user interacts with Widget
  * Declare `Intent` to be executed at a specific time in future

####Intent Resolution
* System receives implicit intent:
  * compares it to intent filters, according to action, data and category

######Action test
* if intent filter got action test, only intents with that acton pass,
* if intent filter has no action test, all intents fail
* if intent has no action, it will pass, if intent filter has one or more actions

######Category test
* `<intent-filter>` can specify zero or more categories
* every category in `Intent` must match a category in `<intent-filter>`, but the reverse is not necessary, so `Intent` with no category will always pass
* Android automatically applies the theCATEGORY_DEFAULT category to all implicit intents passed to startActivity() and startActivityForResult()

######Data test
* `<intent-filter>` can specify zero or more `<intent-filter>` can specify zero or more `<data>` elements
* has:
  * scheme
  * host
  * port
  * path - can have wildcard*



######Intent matching
* Intent filers are used, for example to return all activities with `ACTION_MAIN` and `CATEGORY_LAUNCHER`
