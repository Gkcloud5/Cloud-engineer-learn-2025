
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
* `COPY index.html /usr/share/ngnix/html/index.html` --> Copy your file from folder into the image. to exact spot ngnix 