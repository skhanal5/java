### JMeter UI
* Find the bin directory inside of wherever you installed JMeter
* Invoke `./jmeter.sh`
### Setup
#### 1. Test Plan
* Create a test plan to define a new performance test
#### 2. Thread Group
* Define the # of threads, ramp-up period, loop count, etc.
* Think of this as the number of users
##### Thread Group Options
* Can define how to handle errors
* Define # of threads
* Define a ramp up period: gap between each users' hits
* Loop count: define the number of times a test will run for the number of users
* Scheduler: define the start and end time of the test
### Sampler
* Used to define the type of request you want to invoke
##### HTTP Request Options
* Define endpoint
* Define type of request
* Define path
* Define query params, request body
### Listener
* Allows you to display results about the test  and generate reports
* Typically, plugins are used here