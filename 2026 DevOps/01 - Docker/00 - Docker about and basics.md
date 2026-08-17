
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


### Some Basics command:

* `RUN` --> Run commands during build, install packages, create files.
* `WORKDIR` --> Sets the working folder. all later steps run inside it
* `ENV` -->  `export DB_HOST=...` --> Set environment variable that lives inside the image and the running container
* `EXPOSE` --> documentation only. a label saying which port the app listens
* ``CMD` / `ENTRYPOINT`` --> `ExecStart` --> The command that runs when the container starts. this is what keeps it alive.

```
FROM python:3.13-slim          # base image (pick the current stable tag)
WORKDIR /app                   # cd into /app
COPY requirements.txt .        # copy dependency list in
RUN pip install -r requirements.txt   # install them AT BUILD TIME
COPY . .                       # copy the rest of the app
ENV PORT=5000                  # set a config variable
EXPOSE 5000                    # document: "I listen on 5000"
CMD ["python", "app.py"]       # the power button: start the app
```

