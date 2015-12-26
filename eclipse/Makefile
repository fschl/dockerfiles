build:
	docker build -t fschl/eclipse .

run:
	docker run -it --rm \
		   --net host \
		   -v /tmp/.X11-unix:/tmp/.X11-unix \
		   -e DISPLAY=unix$DISPLAY \
		   -v $HOME/projects/java/workspace:/home/eclipse/workspace \
		   -v $HOME/.eclipse/plugins:/opt/eclipse/plugins \
		   -v $HOME/.eclipse/configuration:/opt/eclipse/configuration \
		   --name eclipse \
		   fschl/eclipse:latest
