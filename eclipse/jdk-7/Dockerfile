FROM java:7

MAINTAINER Frieder Schlesier <fschl.code@gmail.com>

RUN apt-get update && apt-get install -y --no-install-recommends \
        ca-certificates \
        ssh \
        && rm -rf /var/lib/apt/lists/*

RUN wget http://ftp.halifax.rwth-aachen.de/eclipse//technology/epp/downloads/release/mars/1/eclipse-java-mars-1-linux-gtk-x86_64.tar.gz -O /tmp/eclipse.tar.gz -q && \
    echo 'Installing eclipse' && \
    tar -xf /tmp/eclipse.tar.gz -C /opt && \
    rm /tmp/eclipse.tar.gz

ADD run /usr/local/bin/eclipse
RUN chmod +x /usr/local/bin/eclipse

RUN adduser --disabled-password --quiet --gecos '' eclipse \
    && chown -R root:eclipse $INSTALLATION_DIR/eclipse \
    && chmod -R 775 $INSTALLATION_DIR/eclipse

USER eclipse    
CMD /usr/local/bin/eclipse    
