#Services

* app component that performs long running operations in background without UI
* performs a single operation
* does not return result to caller

* comes in two forms:
  * __started__
    * activity has started it by `startService()`
  * __bound__
    * app component binds to it by calling `bindService()`
    * you got client - service interface
    * runs as long as another app component is bound to it
    * multiple components can bind to one service
* there can be services that work like both of the above
* `service` can be started even outside app, (from another app)
* `service` is started with an `intent`
* in Manifest, you can declare service as __private__, blocking access to it from other apps
* Service works on the main thread of its hosting process
* always use an explicit intent when starting or binding your service, and do not declare intent filers for service

####Basics:
* Maketh subclass of Service
* Override some methods:
  * `onStartCommand()`
    * runs when another component requests that the `service` be started by `startService()`
    * once executed, service runs in background forever
    * killed with `stopSelf()` or `stopService()`
  * `onBind()`
    * called by __System__ when another component want to bind with this service, by calling `bindService()`
    * return __null__ if no binding is desired
  * `onCreate()`
    * called whan __service__ is created  first time
  * `onDestroy()`
    * __System__ calls it when service is no longer used
    * clean up any resources here

######Declare your service in the Manifest:
* Like other components, services have to be declared in manifest:
```xml
<manifest ... >
  <application ... >
    <service android:name="foo" /> <!-- class name -->
  <application>
</manifest>
```

####Creating a started service
* A started service is such that another component starts it by calling `startService()`, resulting in the call to `onStartCommand()` method call
* When a service is started, its lifecycle is independent on the component that started it
* service should stop itself when iths jobb is done by `stopSelf()`, or another component can call `stopService()`
* App component like activity can start service by `startService()` and pass an __intent__ to it ti pass any data for it. Service recieves __intent__ in the `onStartCommand()`

* __started service__ can be made by extending two classes:
  * __Service__:
    * Base class for all services
    * When extending this, create a new thread
    * can handle multiple requests simutaneously?
  * __IntentService__:
    * Subclass of `service` that handles all start requests one at a time
    * must implement `onHandleIntent()` that recieves each start request

######Extending the IntentService class
* Best option is to use this
* The `IntentService` does:
  * creates a default worker thread seperate from app main Thread
  * maketh queue that passes one intent at a time to `inHandleIntent()`, so no concurrency here
  * stops service after all start requests are handled, so no need to call `stopSelf()`
  * default implementation for `onBind()` that returns null.
  * default implementation of `onStartCommand()` that sends intent to queue
  ```Java
public class Foo extends IntentService{
  public Foo(){
    super("Foo"); //we pass name of the worker thread
  }
  @Override
  protected void onHandleIntent (Intent intent){
    try{
      //do work
    }
    catch (Exception e){
      //do something
    }
  }
}
  ```

###### Extending the service class
* can handle simultaneous start requests
* for each start request, we use a worker thread and perform job processes one request at a time
```Java
public class Foo extends Service{
  private Looper mServiceLooper;
  private ServiceHandler mServiceHandler;

  //inner class
  private final class ServiceHandler extends Handler {
    public ServiceHandler(Looper Looper){
      super(looper);
    }
    @Override
    public void handleMessage(Message msg){
      try{
        //do stuff
      }catch(Exception e){
        //do stuff
      }
      //Stop service using the startID
      stopSelf(msg.arg1);
    }
  }

  @Override
  public void onCreate(){
    //maketh new thread
    HandlerThread thread = new HandlerThread("someString"m Process.THREAD_PRIORITY_BACKGROUND );
    thread.start();
    mServiceLooper = thread.getLooper;
    mServiceHandler = new ServiceHandler(mServiceLooper);
  }

  @Override
  public int onStartCommand(Intent intent, int flags, int startId){
    Toast.makeText(this, "Service starting", Toast.LENGTH_SHORT).show;
    //do something
    return START_STICKY; //int describes how system should contineue the service if it was killed
  }

  @Override
  public IBinder onBind(Intent intent){
    // we do not provide binding
    return null;
  }

  @Override
  public void onDestroy(){
    Toast.makeText(this, "service done", Toast.LENGTH_SHORT).show();
  }
}

```
######Starting a Sercvice
* You start a service from an activity or another app component by passing an `intent` to `startService()`
```Java
Intent intent = new Intent(this, HelloService.class);
startService(intent);
```
######Stopping a service
* started service must manage its own lifecycle
* system does not stop or destroy the service unless memory needed

####Creating a bound service
* `bound` service allows other app components to bind to it by calling `bindService()` to create a long standing connection
* implement `onBind()`
* when no more app components are __bound__ to the service, it is destroyed by system
* multiple clients can bind to the service at once


####Sending Notifications to the user
* service can call `Toast Notifications` or `Status Bar Notifications`

####Running Service in the foreground
* user is actively aware of this service and thus service is not a candidate for killing when low on memory
* needs having a notification on status bar
* music player is an example
* to start, call `runForeground()`
* to stop, call `stopForeground()`

####Managing the lifecycle of a Service
* __started__ service or a __bound__ service
![pic]()
