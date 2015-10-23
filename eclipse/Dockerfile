FROM java:7

MAINTAINER fschl <friedaar@gmx.de>

ENV DOWNLOAD_URL http://ftp-stud.fht-esslingen.de/pub/Mirrors/eclipse/technology/epp/downloads/release/mars/1/eclipse-java-mars-1-linux-gtk-x86_64.tar.gz
ENV INSTALLATION_DIR /usr/local/ 

RUN wget "$DOWNLOAD_URL" -O /tmp/eclipse.tar.gz && \
    tar -xf /tmp/eclipse.tar.gz -C $INSTALLATION_DIR && \
    rm /tmp/eclipse.tar.gz 

RUN adduser --disabled-password --quiet --gecos '' eclipse \
    && chown -R root:eclipse $INSTALLATION_DIR/eclipse \
    && chmod -R 775 $INSTALLATION_DIR/eclipse

USER eclipse
ENTRYPOINT INSTALLATION_DIR/eclipse/eclipse
