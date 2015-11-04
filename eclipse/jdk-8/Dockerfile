FROM java:8

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

CMD /usr/local/bin/eclipse    
