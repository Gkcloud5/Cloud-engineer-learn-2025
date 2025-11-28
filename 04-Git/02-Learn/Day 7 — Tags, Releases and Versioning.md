
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