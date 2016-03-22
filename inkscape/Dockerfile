FROM alpine:latest
MAINTAINER rasch <me@randyschneck.com>
RUN apk update && apk upgrade && apk add inkscape ttf-dejavu && \
  rm -rf /var/cache/apk/* && \
  adduser -D inkscaper
USER inkscaper
WORKDIR /home/inkscaper
RUN mkdir -p .local/share && \
    touch .local/share/recently-used.xbel
CMD ["/usr/bin/inkscape"]
