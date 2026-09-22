
**Docker runs containers. Docker compose defines and runs a group of related containers as one application**

### Why this exists:
* When one app run it need multiple containers like nginx, python, postgreSQL, redis
	* When running those we have issue like
		* Which port should be exposed?
		* Which containers need to communicate?
		* What environment variable are required?
		* Where should persistent data go?
		* Which network should containers use?
		* How do you recreate everything on another machine?
		* How do you start/stpo the entire application

```
Docker CLI
   |
   | "Create/run this container"
   v
Individual containers


Docker Compose
   |
   | "This is my entire application"
   v
┌─────────┬─────────┬──────────┬─────────┐
│  Nginx  │   App   │ Postgres │  Redis  │
└─────────┴─────────┴──────────┴─────────┘
```

* Docker compose usually return in yaml file
	* It have information about multiple container applications
* Example:
```
services:

	web:
	  image: nginx
	
	app:
	  image: pyhton:3.12
	
	db:
	 image: postgres:16
```