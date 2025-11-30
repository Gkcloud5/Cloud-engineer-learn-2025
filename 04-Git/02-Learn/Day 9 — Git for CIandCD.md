
### 9.1 Overview:
* Git hub tools all do one thing
	* They listen to git events and run automation
	* Some tools
		* Github Actions
		* Gitlab CI
		* Jenkins
		* ArgoCD
		* CircleCI
	* Example of GIT events
		* Push
		* Pull request
		* tag
		* merge
		* branch date

### 9.2 Most common CI/CD triggers:
#### 9.2.1 When code is pushed:
``` yaml
on:
	push:
		branches:
			- main
			- dev
```
* Companies use this to:
	* run tests
	* run security scans
	* run linting

#### 9.2.2 When a PR is created:
```yaml
on:
	pull_request:
		branches:
		  -main
		 
```