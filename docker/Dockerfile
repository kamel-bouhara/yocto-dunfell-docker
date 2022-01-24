FROM ubuntu:16.04

RUN apt -y update &&\
    apt -y upgrade &&\
    apt -y install gawk wget git-core \
           diffstat unzip texinfo gcc-multilib build-essential \
           chrpath socat cpio python python3 python3-pip \
           python3-pexpect xz-utils debianutils iputils-ping \
           libsdl1.2-dev xterm tar locales dos2unix vim git libncurses-dev \
	   screen vim device-tree-compiler bmap-tools
RUN pip3 install kas
RUN pip3 install jsonschema==3.0.2
RUN locale-gen en_US.UTF-8 && update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

ARG UNAME=devuser
ARG USER
ARG UID=1000
ARG GID=1000
RUN echo "Adding new user $UNAME id=$UID gid=$GID"
RUN addgroup --gid $GID $UNAME
RUN adduser --disabled-password --gecos '' --uid $UID --gid $GID $UNAME
COPY init /

USER devuser
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

ENTRYPOINT ["/init"]
