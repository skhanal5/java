### About
* Allows you to define an method argument in a general way instead of an actual value
* This gives you flexibility when mocking/verifying because you capture all arguments that meet that method signature's definition without needing to pass in explicit values
### Mocking
* Typically when stubbing a method we may come up with something like this:
```java
when(mockedList.get(0)).thenReturn("first");
```
* What if we don't care about the argument? What if that is irrelevant to the behavior of the mock?
* Then we can define the method like so:
```java
when(mockedList.get(anyInt())).thenReturn("first");
```
* `anyInt()` means that any index passed into `get()` will return `first`
### Verification 
* Conversely, we can use argument matchers for verifying as well
* For instance, we may have a method like this:
```java
verify(mockedList).get(0);
```
* But, we can instead do this:
```java
verify(mockedList).get(anyInt());
```
