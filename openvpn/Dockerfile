# openvpn client in a container
#
# start from a directory which contains a openvpn config file named 'config.ovpn'
# cert and key files should be in the same directory or relatively referencable
# from the config file
#
# run like
#    docker run -it --rm \
#           --net host \
#           --device /dev/net/tun:/dev/net/tun \
#           --cap-add NET_ADMIN \
#           -v "$PWD":/etc/openvpn \
#           fschl/openvpn:latest config.ovpn

FROM alpine:latest
RUN apk update && apk add \
    openvpn \
    && rm -rf /var/cache/apk/*

WORKDIR /etc/openvpn

ENTRYPOINT ["openvpn"]
