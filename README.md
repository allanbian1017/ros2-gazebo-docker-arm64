# Docker-ROS2

## What is this?

* A Docker container for ROS2 and Gazebo.


## Prerequisites

* docker, docker-compose


## Getting started

```bash
git clone {this-repository}
cd {this-repository}
docker-compose build
docker-compose up -d
docker-compose exec ros2 bash
```

### ROS2

### Gazebo

```bash
gzserver --verbose /opt/ros/galactic/share/gazebo_plugins/worlds/gazebo_ros_diff_drive_demo.world
```

Open another terminal

```bash
ros2 topic pub /demo/cmd_demo geometry_msgs/Twist '{linear: {x: 1.0}, angular: {z: 1.0}}' -1
```


## Set up your workspace

You may better to follow this steps to set up your workspace.
[Creating a workspace — ROS 2 Documentation: Galactic documentation](https://docs.ros.org/en/galactic/Tutorials/Workspace/Creating-A-Workspace.html)


## Other commands

### docker-compose

```bash
docker-compose stop
```

```bash
docker-compose down
```

```bash
docker-compose exec --user root ros2 bash
```
