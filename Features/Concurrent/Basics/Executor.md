### About
* An `Executor` is an interface that represents an object that executes a [[Runnable]] task
* Its contract:
```java
void execute (Runnable command)
```
* An executor decouples task "submission" from how the task is actually run
	* e.g. how threads are used and scheduled
* **Note**: an executor does not require the execution to be asynchronous
	* Think of a very naive impl of the interface
### Examples 
* Executing from the same thread (synchronous)
```java
 class DirectExecutor implements Executor {
   public void execute(Runnable r) {
     r.run();
   }
 }
```
* Asynchronous (spawning a new thread for each task)
```java
 class ThreadPerTaskExecutor implements Executor {
   public void execute(Runnable r) {
     new Thread(r).start();
   }
 }
```
