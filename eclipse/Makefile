build:
	docker build -t fschl/eclipse .

neon:
	docker build -t fschl/eclipse:neon -f Dockerfile.neon .
	mkdir -p $HOME/.eclipse_neon/plugins
	mkdir -p $HOME/.eclipse_neon/configuration
	mkdir -p $HOME/.eclipse_neon/sonar

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
