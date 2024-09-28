### About
* A thread pool maintains a certain number of threads 
	* These threads are waiting for tasks to be allocated for concurrent execution
* You configure the # of threads in advance
	* **Note**: having too many threads in reserve eats up memory
	* Context-switching will be slower
* Other names:
	* replicated workers
	* worker-crew model
* Benefits:
	* Increase performance
	* Avoids latency in execution
### What is the Alternative?
* You could spawn a new thread each time a task arrives
* Disadvantages:
	* Spend more time
	* Consume more system resources in creating and destroying threads than actually doing the task
* In JVM:
	* Creating too many threads at the same time can cause the system to run out of memory 
### Resources
1. [Wikipedia Thread Pool Overview](https://en.wikipedia.org/wiki/Thread_pool)
2. [Geeks for Geeks - Thread Pools](https://www.geeksforgeeks.org/thread-pools-java/)