# Eclipse In A Container

Run Eclipse release _Mars 1_ inside a container on your desktop. This Image uses the official `java`-images. Those are based on `openjdk` **NOT** oracles java implementation!

This Repo contains 2 Dockerfiles, for `java7` and `java8`. Use accordingly to your target platform.

You can preserve configuration and installed plugins by mounting the according volumes.

## Usage

```bash
docker run -it --rm \
--net host \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-e DISPLAY=unix$DISPLAY \
-v $HOME/projects/java/workspace:/root/workspace \
-v $HOME/.eclipse/plugins:/opt/eclipse/plugins \
-v $HOME/.eclipse/configuration:/opt/eclipse/configuration \
--name eclipse \
fschl/eclipse-jdk8
```

Replace the last line with `fschl/eclipse-jdk7` if you want prevent to use java8 features.

## Halp! Somehow starting my container does not work!

The container needs permissions to access X11. The easiesst way is to run

```bash
xhost +local:root
```

I have placed this in my `.bashrc`.

## TODO

- use eclipse docker plugin to run projects in their own containers
- install commonly used plugins
