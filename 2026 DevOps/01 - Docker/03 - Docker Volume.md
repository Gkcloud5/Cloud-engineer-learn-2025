

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

## run docker and go bash

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


```
[root@ip-172-31-4-249 ~]# docker start -ai datatest
root@db2c104b30cb:/# cat /root/myfile.txt
important data
root@db2c104b30cb:/#

```

* Restart first container and reattaches `-a` and `i`. same container and same writable layer

* Docker uses **OverlayFS**.
	* Read-only image at the bottom, thin writable layer per container on top.



## Volume:
* A volume is storage that lives outside the container's writable layer - managed by docker. sitting on the host disk
* Volume is not the part of the disposable layer so deleting the container does not delete the volume the data surives

```
  ┌──────────────────────────┐
  │ WRITABLE LAYER (dies)    │
  ├──────────────────────────┤
  │ IMAGE (read-only)        │
  └──────────────────────────┘
            │
      mount │  /data  ───────►  ┌─────────────────────┐
            ▼                    │  VOLUME (survives)  │  ← lives on host, outside the container
                                 └─────────────────────┘
```

```
docker volume create mydata
docker volume ls

##Mount the volume and write on it
docker run -it --name voltest -v mydata:/data ubuntu bash
```

```
[root@ip-172-31-4-249 ~]# docker volume create mydata
mydata
[root@ip-172-31-4-249 ~]# docker volume ls
DRIVER    VOLUME NAME
local     mydata
[root@ip-172-31-4-249 ~]#

```


```
root@b3bb0cf98e8c:/# df -h
Filesystem      Size  Used Avail Use% Mounted on
overlay         8.0G  2.2G  5.9G  27% /        --> Writable layer - disposable
tmpfs            64M     0   64M   0% /dev
shm              64M     0   64M   0% /dev/shm
/dev/nvme0n1p1  8.0G  2.2G  5.9G  27% /data  --> Volume that shared here
tmpfs           457M     0  457M   0% /proc/acpi
tmpfs           457M     0  457M   0% /sys/firmware

```

