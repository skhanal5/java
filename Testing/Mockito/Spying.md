### About
* Requires you to have an instance of the actual object\
* Invoking a method on a spy, will invoke the actual method (unlike the behavior in [[Mocking]])
	* Alternatively, you can stub this behavior out
* **Note**: behind the scenes when invoking methods on a spy, it is being invoked on a *copy* of the original object
	* This has implications later on
### Usage
#### Construction
```java
List list = new LinkedList();
List spy = spy(list);
```
#### Invocation
```java
spy.add("one") // this will add onto the list
```
#### Stubbing Methods
```java
when(spy.size()).thenReturn(100);
```
### Caution: Stubbing
* Using `when(Object)` to stub a spy will not work as intended since the real method is called
* For example:
```java
// suppose spy is empty
when(spy.get(0)).thenReturn("foo")
```
* If you tried to get the first element, you get an exception so this behavior doesn't even make sense
* what you can do is use `do...|Answer|Throw` methods from Mockito
```java
doReturn("foo").when(spy).get(0)
```
