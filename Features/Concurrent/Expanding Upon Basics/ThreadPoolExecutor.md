### About
* `ThreadPoolExecutor` is a [[ExecutorService]] that executes each task by using one of several pooled threads
* Java recommends you t o use `Executors` while this `ThreadPoolExecutor` offers a lot of configuration options
### Configuration Options
* Core and maximum pool sizes
	* automatically adjusts pool size according to core pool size and max pool size
	* can be changed dynamically
	* `getPoolSize()` and `getCorePoolSize()` and `getMaximumPoolSize()`
		* Latter two have setters
* On demand construction
	* by default, threads are only created and started once a task arrives
	* but you can prestart some threads
		* good to when the pool has a non empty queue
	* `prestartCoreThread()` and `prestartAllCoreThreads()`
* Creating new threads
	* New threads are made using `ThreadFactory`
	* Using a different factory lets you configure threads differently
		* stuff beyond my knowledge
* Keep alive times
	* If there are more core threads than necessary, excess threads are terminated if they have been idle more than the keep alive time
	* Can be set dynamically
	* `getKeepAliveTime(TimeUnit)` and `setKeepAliveTime(TimeUnit)`
* Queuing
	* Can use any type of [[Blocking Queue]] to transfer and hold submitted tasks
		* Queue affects the pool sizing
	* Strategies for queuing
		* Direct handoffs:
			* hand off tasks to threads without holding them
			* If no threads are available for a task, a new thread is always mad 
		* Unbounded queues
			* New tasks will wait in the queue when all core pool size threads are busy
			* **Note**: max pool size doesn't matter here since we will only have core pool size # of threads
		* Bounded queues
			* queue sizes and max pool sizes can swap
			* Large queues + small pools
				* minimizes CPU usage, OS resources, and context-switching overhead
				* but low throughput
			* Small queues + large pools
				* CPUs are more busier
				* but scheduling overhead
* Rejection
	* skipping this one for now
* Hook methods
	* `beforeExecute(Thread, Runnable)` and `afterExecute(Runnnable, Throwable)` lets you run things before and after executing each task
	* `terminated()` lets you do something once the `Executor` is terminated
* Queue maintenance
	* Use `getQueue()` to get access to the queue for monitoring
* Reclamation
	* A pool that isn't being referenced in a program and has no remaining threads can be reclaimed without being shutdown