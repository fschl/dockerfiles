# Run gimp in a contianer
#
# docker run -d \
#	-v /etc/localtime:/etc/localtime:ro \
#	-v /tmp/.X11-unix:/tmp/.X11-unix \
#	-e DISPLAY=unix$DISPLAY \
#	-v $HOME/Pictures:/root/Pictures \
#	--name gimp \
#	jess/gimp
#

FROM debian:sid
MAINTAINER Frieder Schlesier <fschl.code@gmail.com>

RUN apt-get update && apt-get install -y \
        gimp \
        gimp-data-extras \
        gimp-gutenprint \
        gimp-plugin-registry \
        libgimp2.0-dev \
        wget \
        --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*


# GIMP version && separate plugin
# http://www.blackfiveservices.co.uk/separate.shtml
# seems like its not working
# maybe should use this?     https://osdn.net/projects/separate-plus/downloads/47873/separate+-0.5.8.zip/
ENV GIMP_VERSION 2.0
ENV SEPARATE_URL http://www.blackfiveservices.co.uk/linux_resources/separate-gimp2-0.3_linux.tar.gz

RUN wget -q ${SEPARATE_URL} -O /tmp/separate.tar.gz \
    && tar -xzf /tmp/separate.tar.gz -C /usr/lib/gimp/${GIMP_VERSION}/plug-ins/ \
    && rm /tmp/separate.tar.gz
1
ENTRYPOINT [ "gimp" ]
