
```
Tags are how companies mark deployments, releases, rollbacks, hotfixes and trigger pipelines
```

* Tags are permanent sticky notes glued to specific page. they never move. they say "this exact version of the code is release v1.0"

### 7.1 What is tag?
* A `tag` is a label pointing to specific commit.
```
v1.0.0 --> commit 53***
```
* Tags don't move
* Branches move
* Tags stay forever

### 7.2  Types of tags:
#### 7.2.1 Lightweight tag:
* Just a label
* `git tag v1.0.0`

#### 7.2.2 Annotated tag:
* Stores
	* message
	* author
	* date
	* checksum
* `git tag -a v1.0.0 -m "first stable commit`

### 7.3  Semantic Versioning:
```
MAJOR.MINOR.PATCH
```

#### 7.3.1 MAJOR:
* Structure change
* API changed
* Big refactor
* `v1.0.0 --> v2.0.0`

#### 7.3.1  MINOR:
* New feature
* Backward-compatible
* `v1.0.0 --> v1.1.0`


#### 7.3.2 PATCH(Bug fixes):
* `v1.1.0 --> v1.1.1`


### 7.4 How CI/CD uses tags:
* Most real companies deploy when a tag is created
 ```yaml
  on:
  push:
    tags:
      - 'v*.*.*'


  ```
  