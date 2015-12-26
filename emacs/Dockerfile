FROM debian:jessie
MAINTAINER Daisuke Fujita (dtanshi45@gmail.com) <@dtan4>

ENV EMACS_VERSION 24.5
ENV HOME /home/app

# install emacs build deps emacswiki.org/emacs/EmacsSnapshotAndDebian
RUN apt-get update && \
    apt-get install -y wget \
	git \
	autoconf \
	automake \
	libtool \
	texinfo \
	build-essential \
	xorg-dev \
	libgtk2.0-dev \
	libjpeg-dev \
	libncurses5-dev \
	libdbus-1-dev \
	libgif-dev \
	libtiff-dev \
	libm17n-dev \
	libpng12-dev \
	librsvg2-dev \
	libotf-dev \
	libxml2-dev \
	&& \
    wget -qO /tmp/emacs-$EMACS_VERSION.tar.gz http://ftp.gnu.org/gnu/emacs/emacs-$EMACS_VERSION.tar.gz && \
    cd /tmp && \
    tar zxf emacs-$EMACS_VERSION.tar.gz && \
    cd emacs-$EMACS_VERSION && \
    cd /tmp/emacs-$EMACS_VERSION && \
    ./configure && \
    make bootstrap && \
    make install && \
    cd ../ && \
    rm -rf emacs-$EMACS_VERSION* && \
    apt-get autoremove -y mailx texinfo autoconf automake autotools-dev dpkg-dev quilt debhelper sharutils imagemagick wget && \
    rm -rf /var/lib/apt/lists/*

#    ./autogen.sh && \
WORKDIR /home/app

RUN git clone https://github.com/fschl/.emacs.d

CMD ["emacs"] 
#, "--version"]
