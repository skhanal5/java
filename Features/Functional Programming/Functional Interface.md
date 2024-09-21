### About
* An interface that contains only one abstract method is known as a functional interface
* Use the annotation `@FunctionalInterface` on the interface definition
	* This is used to make the definition concrete
	* Compiler will complain if you have more than 1 abstract method in the interface
	* This is optional
* A Lambda expression or a method reference can be used to define an instance of a functional interface
#### Predefined Functional Interfaces
* [[Consumer]]
* [[Predicate]]
* [[Function]]
* [[Supplier]]
### Usage
* Typically you will use one of the ones above unless you need some custom functionality
* When designing libraries and you want to define some generic behavior, you can use a Functional Interface
* When designing methods, you can give users the responsibility of handling the behavior with functional interfaces
	* It can make functions generic in terms of behavior
#### Example
* Below example is of `Collections.forEach` 
* The designer of this function separates two main concerns:
	* The implementation handles iteration
	* The user of the function handles the logic that happens during iteration
```java
Collection<String> strings = Arrays.asList("a", "b", "c");
strings.forEach(s -> System.out.println(s));
```

### Resources
1. [Geeks for Geeks Article](https://www.geeksforgeeks.org/functional-interfaces-java/)
2. [Baeldung Article](https://www.baeldung.com/java-8-functional-interfaces)