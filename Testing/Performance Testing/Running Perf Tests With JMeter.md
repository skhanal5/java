### Locally
* It is generally not recommended to run your performance testing on a local machine while also running your application locally
* Why?
	* Load testing environment eats up resources
	* If CPU/RAM usage spikes, it will affect the application's ability to handle request
	* This will skew performance results
### Preferred Setup
* Install the load generated in another VPS that is in the same subnet as the application