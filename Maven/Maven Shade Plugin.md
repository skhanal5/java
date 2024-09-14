### About
* Official definition:  *This plugin provides the capability to package the artifact in an uber-jar, including its dependencies and to _shade_ - i.e. rename - the packages of some of the dependencies*
### Scenario
* Typically:
	* You provide an artifact with the classes/resources it uses
	* Maven will handle retrieving any additional artifacts that this artifact depends on
	* Results in a bunch of JARs that your app needs in run in addition to the one you have
* Shade plugin:
	* Constructs an uber-jar
	* It takes the dependencies & the content in those dependencies and bundles them with the classes/resources of your artifact
	* Resulting in 1 big JAR file
### Usage
* Why use this?
	* Makes it easy for execution by providing an uber-jar
	* Makes it easy to distribute your project
#### Shading (Another Use Case)
* What about shading dependencies? (*From SO post linked below*)
	* Suppose your library depends on `Bar` version `1.0`
	* You also depend on `Baz` which itself depends on `Bar` version `2.0`
	* The `2.0` version of `Bar` isn't compatible with your library and `1.0` isn't compatible with `Baz`
	* Share plugin handles this by renaming usage of one `Bar` version
		* E.g. `Bar 1.0` will have its classes named from `com.bar` to `com.foo.bar`
	*  Now, `Baz` can use `Bar 2.0` safely
### Configuration Options
#### Include/Exclude (catch all rule)
* Pick and choose what artifacts you want to include/exclude
```xml
<artifactSet>
	<includes>
		<include>...</include>
	</includes>
	<excludes>
		<exclude>
		</exclude>
	</excludes>
</artifactSet>
```
#### Include/Exclude (granular)
* Pick and choose what classes/file you don't want to include from a particular artifact
	* Usually used to remove other files attached to a 
```xml
<filters>
	<filter>
		<artifact>...</artifact>
		<excludes>
			<exclude>...</exclude>
		</excludes>
		<artifact>...</artifact>
		<includes>
			<include>...</include>
		</includes>
	</filter>
</filters>
```
### Resources
1. [Maven Shade Plugin Documentation](https://maven.apache.org/plugins/maven-shade-plugin/)
2. [Maven Shade Plugin SO Post](https://stackoverflow.com/questions/13620281/what-is-the-maven-shade-plugin-used-for-and-why-would-you-want-to-relocate-java)