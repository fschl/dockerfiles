FROM debian:jessie

MAINTAINER fschl <friedaar@gmx.de>

RUN apt-get update && apt-get install -y \
	texlive-full \
    texlive-math-extra \
    --no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

