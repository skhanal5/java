### About
* Using a mock, will create a complete mock
	* The object itself is just a shell of itself
#### Method Behavior
* Invoking the methods as is will not give you the correct behavior
	* For methods that return a value, the mock will produce *some* default value
* Side effects will not happen
* You will have to stub the behavior of any methods you want to invoke on this mock, if you have to produce its natural behavior
### Features
* Mocks remember all interactions
	* You can use this to verify certain things like method calls
### Usage
#### Construction
```java
List mockedList = mock(List.class);
```
#### Verification
```java
mockedList.add("one"); //not stubbed, doesn't actually do anything
verify(mockedList).add("one");
```
#### Stubbing Methods
```java
when(mockedList.get(0)).thenReturn("first");
```
