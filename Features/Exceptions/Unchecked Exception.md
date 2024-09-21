### About
* Exceptions that aren't checked at compile time (lol)
* If these exceptions aren't handled, you will get a **Runtime Error**
* Programmer has a responsibility to catch or specify the exception themselves
* Rule of thumb:
	* A unchecked exception is subclassed by `RuntimeException` or `Error`
#### Usage
* These are exceptions that are caused by programming errors
	* Example: Index out of bounds
#### Programmer Use Case
* If you think the consumer of this application cannot recover from this, make it a unchecked exception
### Resources
1. [Geeks for Geeks Article](https://www.geeksforgeeks.org/checked-vs-unchecked-exceptions-in-java/)
2. [Baeldung Article](https://www.baeldung.com/java-checked-unchecked-exceptions)