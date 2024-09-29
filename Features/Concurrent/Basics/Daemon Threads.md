### About
* Low priority threads that run in the background
	* Usually used to help user threads
* When user threads finish execution, JVM terminates daemon threads regardless of its status
* Rules:
	* Once all user threads are done, the JVM terminates everything including daemon threads
		* daemon threads cannot stop the JVM from exiting