### About
* A `ThreadPoolExecutor` that can schedule commands to run after a delay 
* Delayed tasks execute no sooner than they are enabled
	* But no guarantees when after they are enabled, when they will actually run
* Tasks scheduled for the same execution time run in FIFO order of submission
* **Note**: Setting `maximumPoolSize` has no effect
	* A `ScheduledThreadPoolExecutor` is a fixed-sized pool using `corePoolSize` threads and an unbounded queue