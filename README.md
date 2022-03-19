# Millrace workspace

This ROS package contains (in theory) everything needed to mimic the behavior of the `ur_ws` folder, modified slightly to increase depedency versions and isolate functionality.

## Setup

You can install this package and it's dependencies as follows:
0. Make sure git is setup with SSH authentication, otherwise cloning the private repositories will fail.
1. Grab a copy of [`applevision.rosinstall`](./applevision.rosinstall).
2. Run the following to clone everything into your workspace using [wstool](http://wiki.ros.org/wstool), install dependencies, and build:
```sh
# in catkin_ws
wstool init src
wstool merge -t src applevision.rosinstall
wstool update -t src
rosdep install -y --from-paths src --ignore-src --rosdistro ${ROS_DISTRO}
catkin config -DPYTHON_EXECUTABLE=/usr/bin/python3 -DPYTHON_INCLUDE_DIR=/usr/include/python3.6m -DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.6m.so
catkin config --install
catkin build
# OR
catkin_make
```

## Launching

To launch a simulated robot run:
```sh
roslaunch millrace_moveit_config demo.launch
```

To launch against a real robot run (with a kinematics config already generated):
```sh
# terminal 1
roslaunch ur_robot_driver ur5_bringup.launch robot_ip:=169.254.177.232 kinematics_config:="${HOME}/my_robot_calibration.yaml"
# terminal 2
roslaunch millrace_moveit_config ur5e_moveit_planning_execution.launch
# terminal 3
roslaunch millrace_moveit_config moveit_rviz.launch config:=true
```