# Setup with docker

<a href='https://hub.docker.com/_/golang/'>Golang on Docker hub</a>

```
# docker pull golang:1.6

# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
golang              1.6                 cc0238ad5a56        4 days ago          744.1 MB

# docker run -t -i golang:1.6 /bin/bash
root@b2db41c8fa6e:/go# go version
go version go1.6.2 linux/amd64
```
