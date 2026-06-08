# https://hub.docker.com/_/ros
#FROM ros:galactic

# https://github.com/osrf/docker_images/blob/master/README.md#ros---1
# https://github.com/osrf/docker_images/blob/master/ros/galactic/ubuntu/focal/desktop/Dockerfile

# ros2 galactic amd64 image
# FROM osrf/ros:galactic-desktop

# ros2 galactic arm64 image
FROM arm64v8/ros:galactic-ros-base
SHELL ["/bin/bash", "-c"]

ARG user_id=1000
ARG ros_ws=/home/dockeruser/dev_ws

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    ros-${ROS_DISTRO}-gazebo-* \
    ros-${ROS_DISTRO}-rosbridge-suite \
    python-is-python3 \
    nano \
    less \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m --uid ${user_id} -s /bin/bash dockeruser
USER dockeruser

WORKDIR /home/dockeruser

ENV HOME=/home/dockeruser
ENV PATH="/home/dockeruser/.local/bin:${PATH}"

ENV PYTHONUNBUFFERED=1

RUN echo "source /opt/ros/${ROS_DISTRO}/setup.bash" >> ~/.bashrc

RUN echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc \
    && echo "export _colcon_cd_root=${ros_ws}" >> ~/.bashrc

ENTRYPOINT ["/ros_entrypoint.sh"]

CMD ["sleep", "infinity"]

