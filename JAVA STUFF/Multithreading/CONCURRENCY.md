#CONCURRENCY AKA MULTITHREADING

* Concurrency makes program to have threads, that run on multiple cores, or a single core
* single core multithreading is ok, if some thread may block the execution of other threads. In this case program is allowed to continue, something that is otherwise impossible

----
8 Threads run in parallel

####Lifecycle of a thread
* Thread Lifecycle has multiple stages:
![lc](https://github.com/Jekabz/someNotes/blob/master/RESOURCES/PICTURES/Screenshot%20from%202016-04-16%2023:18:47.png)
* `New` -- not doing anything jet
* `Runnable` -- executes the task
*  `Waiting` -- waits for another thread to finish
  * `Timed waiting` -- waits for an event or waits a specified amount of time
* `Terminated` -- task completed

####Thread priorities
* Each thread has a Priority:
  * MIN_PRIORITY
  * NORM_PRIORITY -- *default*
  * MAX_PRIORITY
* Threads with higher priorities are more likely to be allocated processor time

####Creating Threads
* Threads can be created by implementing `Runnable` interface or by extending `Thread` class
######Implementing Runnable interface:
* Use this if your class is intended to be executed as thread
  * implement `run()` method. This is entry point for a thread, put your business logics in here
  * Make `new` Thread object and instantiate it:
  ```java
Thread(Runnable threadObj, String threadName); //is this legal?
Thread a = new Thread(new TaskA());
  ```
  * start thread object:
  ```java
  a.start();
  ```

  ----
```java
public class MyRunnable implements Runnable {
    public void run() {
        //Code
    }
}
//Started with a "new Thread(new MyRunnable()).start()" call
```
######Extending Thread class:
* Override `run()` method, put your business logics in it
* Call the `start()` method

```java
public class MyThread extends Thread {
    public MyThread() {
        super("MyThread");
    }
    public void run() {
        //Code
    }
}
//Started with a "new MyThread().start()" call
```

######“implements Runnable” vs. “extends Thread”
* `implements Runnable` seems to be preferred, because you only give `Thread` something to run, instead trying to overwrite any ` Thread` behaviour

----
####Thread INSTANCE Methods:
* Important methods in `Thread` class:
  * `public void start()` -- *Starts the thread in a separate path of execution, then invokes the run() method on this Thread object.*
  * `public void run()` -- *business logics goes here*
  * `public final void setName(String name)` -- *Changes the name of the Thread object.*
  * `public final void setPriority(int priority)` -- *sets priority from 1(lowest) to 10(highest)*
  * `public final void setDaemon(boolean on)` -- *true will will make this a Daemon Thread*
  * `public final void join(long milisec)` -- *this thread invokes the second thread, so this thread blocks until second thread terminates or milisec time passes*
  * `public void interrupt()` -- *if thread was blocked for some reason, this makes it to continue execution*
  * `public final boolean isAlive()` -- *thread is alive before it runs to completion*

####Thread STATIC Methods:
* This will perform the operation on the currently running thread;
  * `public static void yield()` -- *currently running thread might yield to any other same priority threads awaiting execution. put this method at a time when one logical part of run() is completed*
  * `public static void sleep(long milisec)` -- *blocks thread for min of milisec time*
  * `public static boolean holdsLock(Object x)` -- *true if Thread holds lock on x*
  * `public static Thread currentThread()` -- *returns a reference to current thread that invoked this method*
  * `public static void dumpStack()` -- *prints stack trace for current thread*
