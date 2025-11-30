
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
		  - main
		  - dev
```

* Companies use this to:
	* block merge if tests fail
	* enforce code review
	* check for vulnerabilities


#### 9.2.3 when a tag is pushed: (Production deploys)
```yaml
on:
	push:
		tags:
			- "v*.*.*"
```
* Meaning:
	* You create tag v.1.2.0
	* CI/CD deploys automatically
	* No manual clicking
	* No human mistakes
	* Install rollback by pushing an older tag


### 9.3 CI/CD Pipeline flow in real companies:
* 