**Note**: Only able to use in Java 17 or above
### About
- Records are classes that serve to be used as a model class (think POJO)
- Denoted by keyword `record` in place of `class`
- All Records are `final`
### Functionality
* All fields in a Record are `private`and `final`
* Provides the following methods:
	* getters
	* constructors
	* equals
	* hashCode
	* toString
* All of the above methods can be overridden by providing your own implementation
* You can also provide your own static/instance methods in addition to the ones the Record provides
### Constructors
* By default, the constructor includes all fields that are in the Record declaration
* You can override the default constructor that the Record provides by explicitly defining your own constructor with all the fields
* Can also define a *compact constructor* whose signature doesn't include the fields as parameters
### Examples
* Basic Record
```
record Rectangle(double length, double width) { }
```
* Record with a constructor implementation
```
record Rectangle(double length, double width) {
    public Rectangle(double length, double width) {
        if (length <= 0 || width <= 0) {
            throw new java.lang.IllegalArgumentException(
                String.format("Invalid dimensions: %f, %f", length, width));
        }
        this.length = length;
        this.width = width;
    }
}
```
### Resources
1. [Record Documentation](https://docs.oracle.com/en/java/javase/17/language/records.html)
