# OpenVPN In A Docker Container

Dockerfile by jpetazzo & [jfrazelle](https://github.com/jfrazelle/dockerfiles/tree/master/openvpn)

# Usage

1. Create an `config.ovpn` file for the connection. _Example below_
2. Place **crt** and **key** files in the same directory (or subdirectory)
3. Run the container with network capabilities, e.g.

```bash
docker run -it --rm \
    --net host \
    --cap-add NET_ADMIN \
    --device /dev/net/tun:/dev/net/tun \
    -v "$PWD":/etc/openvpn \
fschl/openvpn:latest config.ovpn
```

You can replace `-it --rm` with `-d` if you don't want to keep a terminal open vor the VPN connection.

# Example config.ovpn

```
client
dev tun
;proto tcp
proto udp
;remote my-server-2 1194
;remote-random
resolv-retry infinite
nobind

# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
#
# Docker note: use path relative to .ovpn config file
# only in subdirectories
ca your_server_cert.crt
cert your_user_cert.crt
key your_user_key.key

# Downgrade privileges after initialization (non-Windows only)
;user nobody
;group nobody

# Try to preserve some state across restarts.
persist-key
persist-tun

```
