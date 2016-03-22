docker-inkscape
===============

Run inkscape in a docker container.

Build

    git clone https://github.com/randyschneck/docker-inkscape.git
    cd docker-inkscape
    docker build -t rasch/inkscape --rm .

Usage

    docker run --rm -e DISPLAY \
      -u inkscaper \
      -v /tmp/.X11-unix:/tmp/.X11-unix \
      -v $HOME/.Xauthority:/home/inkscaper/.Xauthority \
      --net=host rasch/inkscape
