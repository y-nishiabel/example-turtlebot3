FROM ubuntu:16.04
MAINTAINER Nobuyuki Matsui <nobuyuki.matsui@gmail.com>

ENV PYTHONUNBUFFERED 1

COPY ./kube_entrypoint.sh /opt/kube_entrypoint.sh
COPY ./certs/DST_Root_CA_X3.pem /etc/fiware_ros_turtlebot3_bridge/certs/ca.crt
WORKDIR /opt/ros_ws

RUN apt update && apt upgrade -y && apt install -y git ca-certificates python-setuptools python-pip --no-install-recommends && \
    mkdir -p /opt/ros_ws/src && \
    git clone https://github.com/tech-sketch/fiware_ros_turtlebot3_bridge.git src/fiware_ros_turtlebot3_bridge && \
    git clone https://github.com/tech-sketch/fiware_ros_turtlebot3_msgs.git src/fiware_ros_turtlebot3_msgs && \
    pip install wheel --user && \
    pip install -r /opt/ros_ws/src/fiware_ros_turtlebot3_bridge/requirements/common.txt --user && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get purge -y --auto-remove git
