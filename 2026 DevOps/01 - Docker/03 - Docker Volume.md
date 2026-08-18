

### Why we need it?

* A Docker volume is used to keep data safe outside the container's temporary file system
* What happened to my data when the container is deleted?
	* That's where volumes come in
* Actually containers are designed to be replaceable.

```
Container
   │
   ↓
Volume
   │
   ↓
Database data
```

## run dokcer and go bash

```
docker run -it --name datatest ubuntu bash
```

```

```
