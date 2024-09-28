### About
* Extends [[Executor]]\
* Provides the following additional functionality:
	* Provides method to manage termination
	* Provides method to produce a [[Future]] in order to track progress of async tasks
* The `Executors` class has factory methods for this interface 
### Definition
* There is a bunch so unlike before, only some are shown below
```java
<T> List<Future<T>> invokeAll(Collections<? extends Callable<T>> tasks)

<T> T invokeAny(Collections<? extends Callable<T>> tasks)

boolean isShutdown()

boolean isTerminated()

void shutdown()

Future<?> submit(Runnable task)

<T> Future<T> submit(Callable<T> task)
```
#### Shutdowns
* `ExecutorService` can be shutdown
	* New tasks are rejected
* `shutdown()` allows waiting/submitted tasks to continue 
* `shutdownNow()` prevents waiting tasks from starting and stops currently executing tasks
* **Best practice:** invoke a shutdown method when your done to get resources back