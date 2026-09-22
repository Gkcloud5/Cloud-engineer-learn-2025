
**Docker runs containers. Docker compose defines and runs a group of related containers as one application**

### Why this exists:
* When one app run it need multiple containers like nginx, python, postgreSQL, redis
	* When running those we have issue like
		* Which port should be exposed?
		* Which containers need to communicate?
		* What environment variable are required?
		* Where should persistent data go?
		* Which network should containers use?
		* How do you recreate everything