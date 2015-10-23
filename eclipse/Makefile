build-jdk-8:
	rm -rf Dockerfile 2>/dev/null
	cp jdk-8/Dockerfile ./Dockerfile
	docker build -t fschl/eclipse-jdk8 .

build-jdk-7:
	rm -rf Dockerfile 2>/dev/null
	cp jdk-7/Dockerfile ./Dockerfile
	docker build -t fschl/eclipse-jdk7 .

build-jdk-user:
	rm -rf Dockerfile 2>/dev/null
	cp jdk-7/Dockerfile2 ./Dockerfile
	docker build -t fschl/eclipse-user .
