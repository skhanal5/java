### About
* A `Future` is the result of any async operation
* It exposes the following methods:
```java
boolean cancel(boolean mayInterruptIfRunning)

V get()

V get(long timeout, TimeUnit unit)

boolean isCancelled()

boolean isDone()
```
* These methods do the following:
	* check to see if the computation is done
	* Wait for its completion
	* Or get the result of the computation
* `get()` will retrieve the result iff it is completed 
	* This is *blocking*
* `cancel()` obviously cancels
### Usage
* If you want to use `Future` in a way where you don't produce a result, define it like so:
	* declare your type `Future<?>` and return `null` from the task