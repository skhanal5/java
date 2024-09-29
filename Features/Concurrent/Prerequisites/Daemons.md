### About
* A program that runs as a background process instead of being under direct control (straight from Wikipedia)
* Conventions:
	* process names that end with a *d* are daemons 
	* Examples:
		* syslogd
		* sshd
* Daemons are spawned at boot time
* Daemons can be used to perform tasks at scheduled times
	* Example: Cron job