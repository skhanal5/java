### About
* A concurrent collection is:
	* thread safe
	* not governed by a exclusion lock
* A synchronized collection is:
	* governed by a exclusion lock
	* Prevents all access to a collection via one lock
	* **Note**: does not scale well
### Usage
* Use a concurrent collection when:
	* When you need multiple threads to access a common collection