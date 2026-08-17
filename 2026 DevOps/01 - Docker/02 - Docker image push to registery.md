

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


* orphan with no name and no tag --> `<none>  <none>    6e987c2b0e5d   2 days ago     161MB`


## Push to github docker:

```
docker push gokulkrish07/gk-website:v1
```

* You must push the **full name** (`username/image:tag`), not the short one

```
[root@ip-172-31-1-28 ~]# docker push gokulkrish07/gk-website:v1
The push refers to repository [docker.io/gokulkrish07/gk-website]
589ac4f6865d: Pushing [==================================================>]  4.096kB
589ac4f6865d: Pushed
6b6d932908c0: Mounted from library/nginx
df8fa2414ce6: Mounted from library/nginx
896b45bbcb55: Mounted from library/nginx
ca128593f615: Mounted from library/nginx
4647e8109078: Mounted from library/nginx
9df56c3b59f5: Mounted from library/nginx
6f9432833129: Mounted from library/nginx
v1: digest: sha256:5c9195faa8f705a188b2b9f4c1a723832ff267548a47b40b83a1f8f778e8e3f8 size: 1985
[root@ip-172-31-1-28 ~]#
[root@ip-172-31-1-28 ~]#
```

