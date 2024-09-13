### About
* Used for integration tests
* You can use the following phases in the Maven lifecycle to setup integration tests
	* pre-integration-test
	* integration-test
	* post-integration-test
	* verify
* Use `mvn verify` to run the tests
* Tests generate reports in `target/failsafe-reports/*`
### Conventions
- Class names ending with `IT` is used to denote an integration test
### Test Configuration
#### Cucumber
- Just setup a typical Cucumber runner class and run with `mvn verify`
### Plugin Configuration

#### Including Tests
* Set `<includes></includes>` in your plugin configuration
* Example:
```xml
<configuration>
	<includes>
		<include>...</include>
	</includes>
</configuration>
```
#### Excluding Tests
* Set `<excludes></excludes>` in your plugin configuration
* Example:
```xml
<configuration>
	<excludes>
		<exclude>...</exclude>
	</excludes>
</configuration>
```
#### Skipping Tests
- Set `<skipITs>true<skipITs>` in your plugin configuration
- Or use a property `<skipITs>${skipTests}</skipITs>`
	- Run with `mvn install -DskipTests=false`
### Executing Tests
#### Skipping Testing
*  `mvn install -DskipIts`
#### Running Specific Tests
* `mvn -Dit.test=[name of test] verify`
#### Rerunning Failing Tests
* `mvn -Dfailsafe.rerunFailingTestsCount=2 verify
### Resources
1. [Maven Failsafe Plugin](https://maven.apache.org/surefire/maven-failsafe-plugin/)
### TODO
- Parallel test execution