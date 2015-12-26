# golang:1.5 image with added appArmor
# so you can use it to run docker commands
#
# docker run -it --rm \
# -v /var/run/docker.sock:/var/run/docker.sock \
# -v $(which docker):/bin/docker \
# -v "$(pwd)":/usr/src/app \
# -w /usr/src/app
# fschl/golang-dind go "@$"

FROM golang:1.5

MAINTAINER fschl <fschl.code@gmail.com>

RUN apt-get update && apt-get install -y \
    libapparmor-dev \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src/app
