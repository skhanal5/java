### About
- A Maven Lifecycle is the process of building and distributing a project
- There are three built-in lifecycles
	- `default`
		- for deployment
	- `clean`
		- for cleaning
	- `site`
		- to make your project's website
### Phases
* Each build lifecycle contains build phases
* Each phase is conducted in sequential order
### Command Line
* You can trigger a phase in the lifecycle via the cli
* For example:
	* if you want a JAR file then do:
		* `mvn package`
	* if you want to test a file then do:
		* `mvn test`\
	* etc.
* For the phase the you specify, all preceding phases in the lifecycle are also triggered
* For example:
	* `mvn verify` triggers `validate`, `compile`, `package` , etc. in the `default` lifecycle
### Multi Module Setting
* In case you have a multi-module project, if you invoke a command in the root directory, it will trigger in each submodule as well
	* For example, doing `mvn clean package` will invoke `clean` in each submodule and then trigger `deploy`
### Plugin Goals
 * A plugin goal is a specific task, more granular than a phase
 * You can bind a goal onto a build phase
	 * Alternatively, it might not be bound at all
		 * This means to use it, you must trigger it directly (see below)
	 * If you bind a goal to multiple phases, it will be triggered in each phase
* If a phase has no goals then it is **not executed**
* You can trigger a phase from the command like so:
	* `mvn clean dependency:copy-dependencies package`
	* `copy-dependencies` is the goal
#### Aside: Not all goals are meant to be triggered
* E.g. `pre-*`, `post-*`, `process-*` is used to stage/modify an environment for another a goal
* It has no meaning when invoked individually
### Usage of Plugin Goals
### Packaging
- Set the packaging for your project
- This will bind goals to different build phases in a lifecycle
#### Plugins
* Add plugins in your project
* Plugins come with goals that may be configured to a particular phase
* **Important:** Adding the plugin is not enough, you need to tell the plugin which goals you want to invoke\
* The goals you pick will be bound to the goals that are included in the packaging you picked
	* plugin goals + packaging goals -> packaging phases -> packaging lifecycle
	* By default, the packaging goals are triggered first if you also bind a plugin goal to the same phase
### Resources
1. [Maven Lifecycle Documentation](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)
