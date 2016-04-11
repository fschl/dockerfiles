FROM java:8

MAINTAINER Frieder Schlesier <fschl.code@gmail.com>

RUN apt-get update && apt-get install -y --no-install-recommends \
        ca-certificates \
        openjfx \
        && rm -rf /var/lib/apt/lists/*

ENV INSTALL_DIR /home/eclipse/

RUN adduser --disabled-password --quiet --gecos '' eclipse \
    && mkdir -p $INSTALL_DIR

RUN wget http://download.gluonhq.com/scenebuilder/8.1.1/SceneBuilder-8.1.1.jar -O $INSTALL_DIR/scenebuilder.jar

RUN chown -R root:eclipse $INSTALL_DIR/scenebuilder.jar \
    && chmod -R 775 $INSTALL_DIR/scenebuilder.jar

USER eclipse

WORKDIR /home/eclipse/workspace

CMD ["/usr/bin/java", "-jar", "/home/eclipse/scenebuilder.jar"]
