FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV ROS_DISTRO=noetic

RUN apt-get update && apt-get install -y --no-install-recommends gnupg2 dirmngr && \
    apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654 && \
    sh -c 'echo "deb http://packages.ros.org/ros/ubuntu focal main" > /etc/apt/sources.list.d/ros-latest.list'

RUN apt-get update && apt-get install -y --no-install-recommends \
    cmake \
    zip \
    unzip \
    git \
    tmux \
    wget \
    curl \
    vim \
    build-essential \
    ros-$ROS_DISTRO-ros-base && \
    rm -rf /var/lib/apt/lists/*

RUN echo '#!/bin/bash\nset -e\nsource "/opt/ros/noetic/setup.bash"\nexec "$@"' > /ros_entrypoint.sh && \
    chmod +x /ros_entrypoint.sh

ENTRYPOINT ["/ros_entrypoint.sh"]

CMD ["bash"]
