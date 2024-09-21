#### Rules
1. Use checked exception and unchecked exceptions accordingly
2. If you have to handle an exception, do one of these:
	1. rethrow it
	2. construct a new exception and pass the current on in the constructor
	3. log and return something (only fits in some specific use cases)
3. Expanding upon sub point 2: do not obscure the original cause of an exception
4. Do not throw `Exception` in vain
	1. Throw the specific Exception for your use case
