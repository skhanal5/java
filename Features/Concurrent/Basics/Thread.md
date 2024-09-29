### About
* A thread is a thread of execution in a program
* Each thread has a *priority*, which determines when it will be executed in respect to other threads
* Each thread may be marked as a *daemon*
	* [[Daemon Threads]]
* Rules:
	* Non-daemon threads spawn other non-daemon threads
	* Daemon threads spawn other daemon threads
* `Thread` is a class that encapsulates the above with implementation
#### Aside: JVM & Threads
* When the JVM starts:
	* There is a single non-daemon thread (used to call main usually)
	* JVM continues to executes threads until one of the following happens:
		* exit method is inovked and security manager allows for exit operation
		* all non-daemon threads have died
			* each successfully by returning from the call to the run method or by throwing an exception
### Creating Threads
* There are two ways of making a `Thread`
#### By Subclassing Thread
* You can declare a class to be a subclass of `Thread` and override the `run` method
* Example:
```java
     class PrimeThread extends Thread {
         long minPrime;
         PrimeThread(long minPrime) {
             this.minPrime = minPrime;
         }

         public void run() {
             // compute primes larger than minPrime
              . . .
         }
     }
```
* To run it:
```
PrimeThread p = new PrimeThread(143);
p.start();
```
#### Implementing Runnable
* You can implement [[Runnable]] which forces you to implement the `run` method