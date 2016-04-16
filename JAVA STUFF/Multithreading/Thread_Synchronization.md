#Thread Synchronization
* Multiple threads could access the same resource at the same time and produce unexpected results
* `monitor`:
  * mechanism to control concurrent access to an object
  * This prevents Threads 1 and 2 accessing the monitored (synchronized) section at the same time. One will start, and monitor will prevent the other from accessing the region before the first one finishes.

----
* `synchronized` block:
  * Keep shared resources within this block
  ```java
synchronized(objectidentifier) {
   // Access shared variables and other shared resources
}
  ```
