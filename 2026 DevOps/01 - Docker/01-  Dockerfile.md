
* A docker file is a bash script that builds a machine. 
	* How we set up a fresh server by hand.
	* start from some base OS, copy your files in, install packages, set the startup command. A Dockerfile is that same list of setup steps, written down. Docker reads it top to bottom and follows each instruction to assemble an image.
* dockerfile specifc word for "where do we start"
* **Base Image:** it's foundation layer we built on

### Create dockerfile on test folder:

```
cat > Dockerfile << 'EOF'
FROM ngnix:latest
COPY index.html /usr/share/ngnix/html/index.html
EOF
```

* `FROM ngnix:latest` --> Stare from the ngnix image.
* `COPY index.html /usr/share/ngnix/html/index.html` --> Copy your file from folder into the image. to exact spot ngnix server.

![[Pasted image 20260815232709.png]]

**Baking files into the image makes it portable and self contained, the image runs identically anywhere because it carries its own content. that's the whole reason containers beat just copy files to a server**

```
BUILD:
docker build -t gk-website .
```

* `docker build -->` Read the dockerfile and assemble an image from it
* `-t gk-website` `-->` tag(name) the image gk-website. 
* `. -->` build context. dockerfile and files are in the current folder. dot means here

```

[root@ip-172-31-1-28 my-first-image]# docker build -t gk-website .
[+] Building 0.2s (7/7) FINISHED                                                                      docker:default
 => [internal] load build definition from Dockerfile                                                            0.0s
 => => transferring dockerfile: 164B                                                                            0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                 0.0s
 => [internal] load .dockerignore                                                                               0.0s
 => => transferring context: 2B                                                                                 0.0s
 => [internal] load build context                                                                               0.0s
 => => transferring context: 91B                                                                                0.0s
 => CACHED [1/2] FROM docker.io/library/nginx:latest                                                            0.0s
 => [2/2] COPY index.html /usr/share/nginx/html/index.html                                                      0.1s
 => exporting to image                                                                                          0.0s
 => => exporting layers                                                                                         0.0s
 => => writing image sha256:012c1c95b99a4721df05585ddf5e42b9c1938f0a8a125435b4d4fe010764469f                    0.0s
 => => naming to docker.io/library/gk-website                                                                   0.0s
[root@ip-172-31-1-28 my-first-image]#


```


### Run the image:

```
docker run -d -p 8080:80 --name mysite gk-website
```

