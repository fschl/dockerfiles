build-jdk-8:
	rm -rf Dockerfile 2>/dev/null
	cp jdk-8/Dockerfile ./Dockerfile
	docker build -t fschl/eclipse-jdk8 .

build-jdk-7:
	rm -rf Dockerfile 2>/dev/null
	cp jdk-7/Dockerfile ./Dockerfile
	docker build -t fschl/eclipse-jdk7 .

run-java7:
	docker run -it --rm \
		   --net host \
		   -v /tmp/.X11-unix:/tmp/.X11-unix \
		   -e DISPLAY=unix$DISPLAY \
		   -v $HOME/projects/java/workspace:/root/workspace \
		   -v $HOME/.eclipse/plugins:/opt/eclipse/plugins \
		   -v $HOME/.eclipse/configuration:/opt/eclipse/configuration \
		   --name eclipse \
		   fschl/eclipse-jdk7:latest

run-java8:
	docker run -it --rm \
		   --net host \
		   -v /tmp/.X11-unix:/tmp/.X11-unix \
		   -e DISPLAY=unix$DISPLAY \
		   -v $HOME/projects/java/workspace:/root/workspace \
		   -v $HOME/.eclipse/plugins:/opt/eclipse/plugins \
		   -v $HOME/.eclipse/configuration:/opt/eclipse/configuration \
		   --name eclipse \
		   fschl/eclipse-jdk8:latest
