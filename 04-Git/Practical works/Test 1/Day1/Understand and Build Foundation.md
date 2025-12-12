
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
	* It can SSH in