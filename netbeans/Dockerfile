FROM ubuntu:16.04

MAINTAINER Frieder Schlesier "fschl.code@gmail.com"
#MAINTAINER Fabio Rehm "fgrehm@gmail.com"

RUN sed 's/main$/main universe/' -i /etc/apt/sources.list && \
    apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:webupd8team/java -y && \
    apt-get update && \
    echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
    apt-get install -y \
        ca-certificates \
        oracle-java8-installer \
        libxext-dev \
        libxrender-dev \
        libxtst-dev \
        sudo && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*

RUN apt-add-repository ppa:mosquitto-dev/mosquitto-ppa \
    && apt-get update && apt-get install -y mosquitto \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/*

ADD state.xml /tmp/state.xml

ENV NETBEANS_VERSION 8.0.1
RUN wget http://download.netbeans.org/netbeans/${NETBEANS_VERSION}/final/bundles/netbeans-${NETBEANS_VERSION}-linux.sh -O /tmp/netbeans.sh -q && \
    chmod +x /tmp/netbeans.sh && \
    echo 'Installing netbeans' && \
    /tmp/netbeans.sh --silent --state /tmp/state.xml && \
    rm -rf /tmp/*

ADD run /usr/local/bin/netbeans

RUN chmod +x /usr/local/bin/netbeans && \
    mkdir -p /home/developer && \
    echo "developer:x:1000:1000:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:1000:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown developer:developer -R /home/developer


USER developer
ENV HOME /home/developer
WORKDIR /home/developer
CMD ["/usr/local/bin/netbeans"]
