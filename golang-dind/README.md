# fschl/Golang-dind

A docker image based on `golang:1.5` with _AppArmor_ installed. I use this to programatically manage docker containers from _Go_ programs.

## Usage

```
docker run -it --rm \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v $(which docker):/bin/docker \
    -v "$(pwd)":/usr/src/app \
    -w /usr/src/app
 fschl/golang-dind go "@$"
```

and then do some crazy docker stuff in  _Go_

```golang
out, err2 := exec.Command("docker", "images").Output()
```
