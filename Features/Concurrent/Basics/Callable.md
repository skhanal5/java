### About
* Callable is a [[Functional Interface]] that returns a result and can throw an exception
* Very similar to [[Runnable]], only differences:
	* Runnable doesn't produce a return value
	* Runnable cannot throw a [[Checked Exception]]
* Definition:
```java
V call()
```