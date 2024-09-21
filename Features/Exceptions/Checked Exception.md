### About
* Exceptions that are checked at **compile-time**
* If any piece of code throws a checked exception, you have one of two options:
	* Handle the exception explicitly with a try-catch
	* Declare the method throws the exception
* Or you will get a compile-time error
* These exceptions are subclasses of `Exception`
	* Good examples:
		* `IOException`
		* `SQLException`
	
#### Fully Checked Exceptions
* All child classes are also checked
#### Partially Checked Exceptions
* Some child classes are unchecked
### Usage
* Used to indicate that something actually broke (typically outside of the scope of the program)
	* Think resources, network connections, etc. 
#### Programmer Use Case
* If you think the consumer of this application can recover, make it a checked exception
#### Consuming a Checked Exception
* Wrap the checked exception with a [[Unchecked Exception]] (lol)
```java
try {
	...
} catch (IOException e) {
	throw new RuntimeException("...", e);
}
```

### Resources
1. [Geeks for Geeks Article](https://www.geeksforgeeks.org/checked-vs-unchecked-exceptions-in-java/)
2. [Baeldung Article](https://www.baeldung.com/java-checked-unchecked-exceptions)