# Run skype in a container, requires pulseaudio
# (but I have a container for that)
# most work by @jfrazelle
# sadly, ubuntu isn't as simple as debian...
#     
# docker run -d \
#        -v /dev/shm:/dev/shm \
#        -v /etc/machine-id:/etc/machine-id \
#        -v /run/user/1000/pulse:/run/user/1000/pulse \
#        -v /var/lib/dbus:/var/lib/dbus \
#        -v ~/.pulse:/root/.pulse \
#        -v /etc/localtime:/etc/localtime:ro \
#        -v /tmp/.X11-unix:/tmp/.X11-unix \
#        -e DISPLAY=unix$DISPLAY \
#        --device /dev/video0 \
#        --device /dev/snd \
#        --name skype \
#        --net host \
#        fschl/skype
#
FROM debian:jessie

# Tell debconf to run in non-interactive mode
ENV DEBIAN_FRONTEND noninteractive

# Setup multiarch because Skype is 32bit only
# Make sure the repository information is up to date
RUN dpkg --add-architecture i386 && \
	apt-get update && apt-get install -y \
	curl \
	--no-install-recommends

# Install Skype
RUN curl http://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb > /usr/src/skype.deb
RUN dpkg --force-depends -i /usr/src/skype.deb && \
	apt-get install -fy \
	&& rm -rf /var/lib/apt/lists/*

# Start Skype
ENTRYPOINT ["skype"]
