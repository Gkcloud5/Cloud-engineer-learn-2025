
**Docker is a isolated process that helps to run a app without any issue. it has dependencies, config, env values to app run**


* Docker is not program - it's two
	* Docker is command that client type
	* Background service called `dockerd`. it's daemon, tha's does the heavy lifting, building images, running containers, all of it.
		* It runs quietly in the background.


```
[root@ip-172-31-1-28 ~]# docker ps CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES [root@ip-172-31-1-28 ~]#
```

#### Running docker:
```
docker run hello-world
```
* **Look local first** → not found → **pull the image** from the registry (this only happens the first time).
* **Create a container** from that image — a fresh, running instance of the template.
* **Run it, stream the output** back through the daemon to your terminal (the kitchen cooked, the waiter delivered).

**Image = the read-only template. Container = a running instance made from it.**


### Commands:

```
yum install docker -y
systemctl start docker
systemctl enable docker
docker ps
docker run **Dcoker name**
docker images  ##see images in machine
docker ps -a  ##flag all getting information
docker rm **container name**
docker rmi **Image name**
```


