# Setup with docker

<a href='https://hub.docker.com/_/golang/'>Golang on Docker hub</a>

```
# docker pull golang:1.6

# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
golang              1.6                 cc0238ad5a56        4 days ago          744.1 MB

# docker run -t -i -v "$PWD":/go/src -w /go golang:1.6 /bin/bash
root@b2db41c8fa6e:/go# go version
go version go1.6.2 linux/amd64
```

-v [host dir : container dir]
-w [work dir in container]

for convinience export build result path
```
export PATH=$PATH:$GOPATH/bin
```

# Build Project

```
go install <path-under-src>
```

