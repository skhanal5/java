### Principles
1. Tests should be easy to read
	1. clear
	2. simple
	3. density of expression (short)
### Bad Unit Test Example
From *Clean Code: A Handbook of Agile Craftsmanship* 
```
   public void testGetPageHieratchyAsXml() throws Exception  
   {  
  
     crawler.addPage(root, PathParser.parse(“PageOne”));  
     crawler.addPage(root, PathParser.parse(“PageOne.ChildOne”));  
     crawler.addPage(root, PathParser.parse(“PageTwo”));  
  
     request.setResource(“root”);  
     request.addInput(“type”, “pages”);  
     Responder responder = new SerializedPageResponder();  
     SimpleResponse response =  
       (SimpleResponse) responder.makeResponse(  
          new FitNesseContext(root), request);  
     String xml = response.getContent();  
  
     assertEquals(“text/xml”, response.getContentType());  
     assertSubString(“<name>PageOne</name>”, xml);  
     assertSubString(“<name>PageTwo</name>”, xml);  
     assertSubString(“<name>ChildOne</name>”, xml);  
   }
```
* Too much going on in this test, hard to determine what it is even testing
### Good Unit Test Example
From *Clean Code: A Handbook of Agile Craftsmanship* 
```
 public void testGetPageHierarchyAsXml() throws Exception {  
     makePages(“PageOne”, “PageOne.ChildOne”, “PageTwo”);  
  
     submitRequest(“root”, “type:pages”);  
  
     assertResponseIsXML();  
     assertResponseContains(  
       “<name>PageOne</name>”, “<name>PageTwo</name>”, “<name>ChildOne</name>”  
     );  
   }
```
* Good because it follows the *build-operate-check* pattern
* Refactor functions into this patern
#### DSL for Testing
* When do this type of routine refactoring, you will have a set of common utility functions that will be used to build new tests
* These functions are wrappers around the underlying API that you want to test
##### DSL Example
(From *Clean Code: A Handbook of Agile Craftsmanship*)
```
   @Test  
     public void turnOnLoTempAlarmAtThreashold() throws Exception {  
       hw.setTemp(WAY_TOO_COLD);  
       controller.tic();  
       assertTrue(hw.heaterState());  
       assertTrue(hw.blowerState());  
       assertFalse(hw.coolerState());  
       assertFalse(hw.hiTempAlarm());  
       assertTrue(hw.loTempAlarm());  
     }
```
After refactoring:
```
  @Test  
     public void turnOnLoTempAlarmAtThreshold() throws Exception {  
       wayTooCold();  
       assertEquals(“HBchL”, hw.getState());  
     }
```
* "HBchL" is apart of this test suite's DSL
### Given,When,Then
* Another way of expressing tests, similar to before-operate-assert
```
  public void testGetPageHierarchyAsXml() throws Exception {  
       givenPages(“PageOne”, “PageOne.ChildOne”, “PageTwo”);  
  
       whenRequestIsIssued(“root”, “type:pages”);  
  
       thenResponseShouldBeXML();  
   }
```
#### Assertions
- Try to minimize the number of assertions per unit test
- Each unit test should only test a single concept
### F.I.R.S.T.
* Fast
	* slow tests are annoying to run frequently
	* write tests that run quickly
* Independent
	* tests should not depend on each other
	* hard to diagnose issues if there are dependencies
* Repeatable
	* Should be able to run the same tests in any environment
* Self-Validating
	* Tests should have a boolean output
	* Should not have to compare text output/log files
* Timely
	* Write test code before writing the production code 
	* If you write tests after the code, it might be hard to write test code
		* Perhaps the prod code isn't written in a testable manner
* 