# Eclipse In A Container

Run Eclipse release _Mars 1_ inside a container on your desktop. This Image is based on the official `java`-image. Those are based on `openjdk` **NOT** oracles java implementation!
_OpenJFX_ is also installed.

You can preserve configuration and installed plugins by mounting the according volumes.

## Usage

```bash
docker run -it --rm \
--net host \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-e DISPLAY=unix$DISPLAY \
-v $HOME/projects/java/workspace:/home/eclipse/workspace \
-v $HOME/.eclipse/plugins:/opt/eclipse/plugins \
-v $HOME/.eclipse/configuration:/opt/eclipse/configuration \
--name eclipse \
fschl/eclipse
```

## Halp! My container doesn't start!

The container needs permissions to access X11. The easiest way is to run

```bash
xhost +local:root
```

I have placed this in my `.bashrc`.

## TODO

- use eclipse docker plugin to run projects in their own containers
- install commonly used plugins
