

**https://hub.docker.com/repositories/gokulkrish07


* It's a central shelf where images lives 
	* So any machine can pull them.

## Tag image in hub name

```
docker tag gk-website gokulkrish07/gk-website:v1
```

```
[root@ip-172-31-1-28 ~]# docker images
REPOSITORY                TAG       IMAGE ID       CREATED        SIZE
gokulkrish07/gk-website   v1        012c1c95b99a   2 days ago     161MB
gk-website                latest    012c1c95b99a   2 days ago     161MB
<none>                    <none>    6e987c2b0e5d   2 days ago     161MB
nginx                     latest    5253dc86cc93   12 days ago    161MB
hello-world               latest    e2ac70e7319a   4 months ago   10.1kB
[root@ip-172-31-1-28 ~]#
```


* orphan with no name and no tag --
