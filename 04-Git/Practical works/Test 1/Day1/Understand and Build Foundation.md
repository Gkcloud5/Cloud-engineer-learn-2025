
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
* Docker contain entire app:
	* Code
	* Dependencies
	* Runtime(Node, python, etc)
* Docker Image:
	* A recipe or package of app
* Docker container:
	* A running instance of the image
* Why we use docker:
	* It runs the same way everywhere - laptop, VPS, github actions

## 1.4 What is container registry:
* It's like a storage place of docker images
* Example:
	* Docker Hub
	* Github container registry
	* AWS ECR
* Why we need registry:
	* VPS must download the new docker image during deployment
	* It can only download from a registry
* So Pipeline does this:
	* 1. Build docker image
	* 2. Push image --> GHCR
	* 3. VPS pulls the image from GHCR
	* 4. Run container

## 1.5 What deployment looks like in VPS:
* Steps in deployment
	* 1. VPS is connects to GHCR
	* 2. It downloads the latest Docker image
	* 3. It stops the old container
	* 4. It starts the new container
* Build --> Scan --> push --> deploy to VPS