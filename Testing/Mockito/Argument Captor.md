### About
* Allows you to capture an argument passed to another method
* Use case: 
	* We are testing a method and inside that method, we want to capture the argument passed into another method
	* We cannot access that argument outside of the method though
### Usage

#### Creating a Argument Captor
* `ArgumentCaptor<U> argument = ArgumentCaptor.forClass(U.class)`
#### Using the Argument Captor
* `verify(mock).doSomething(argument.capture())`
* The `mock` here is the underlying object that invokes the method `doSomething` with the argument of interest
* This needs to be readily accessible to us, otherwise this pattern won't work
	* Use Dependency Injection
* Observe: we invoke `capture()` on the captor
#### Getting the value of the argument captor
* `argument.getValue()`
### Full Example
```
ArgumentCaptor<Person> argument = ArgumentCaptor.forClass(Person.class);
verify(mock).doSomething(argument.capture());
assertEquals("John", argument.getValue().getName());
```
### Resource
1. [Baeldung Argument Captor](https://www.baeldung.com/mockito-argumentcaptor)
2. [Mockito Example](https://site.mockito.org/javadoc/current/org/mockito/ArgumentCaptor.html)