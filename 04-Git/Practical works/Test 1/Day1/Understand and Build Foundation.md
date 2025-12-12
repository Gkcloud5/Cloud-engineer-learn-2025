
## 1.1 Understand the Big picture
### 1.1.1What is CI/CD?
* CI/CD means automating workflow
	* CI - Continuous Integration -> Automatically build and test code whenever push to github
	* CD - Continuous Deployment -> Automatically deploy code to production environment
* Pipeline will do all the things


## 1.2 What github actions does:
* It's automation robot inside github
* Whenever push code:
	* It can build app
	* It can build docker image
	* It can scan for security issues
	* It can push image to GHCR
	* It can SSH into your VPS and deploy the container
* Why:
	* Because everything happens automatically - no manual typing commands on your VPS every time.

## 1.3 What Docker images and containers are:
* 