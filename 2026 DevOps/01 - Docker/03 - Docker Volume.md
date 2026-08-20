

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
[root@ip-172-31-4-249 ~]# docker run -it --name datatest ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu

617772c7d19b: Pull complete
a7fb98a8eddd: Pull complete
Digest: sha256:678c6550cc43645e08669028bc177f50be4e7c5b8cca677067b1914d4afc7a03
Status: Downloaded newer image for ubuntu:latest

root@db2c104b30cb:/#
```


* `-if` --> Interactive terminal. `-i` keeps input open, `-t` gives you terminal.
* `ubuntu` --> The image
* `bash` --> command to run: a shell.

* Every container gets its own thin writable layer stacked on top of the shared read only image
* Anything we can create, edit, delete inside a container goes into that container's layer.

```
   IMAGE (read-only, frozen)          ← ubuntu's files. NEVER changes.
   ─────────────────────────
   CONTAINER writable layer (on top)  ← your myfile.txt went HERE
```

