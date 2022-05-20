# Millrace workspace

This ROS package contains URDF and launchfiles designed to work with the AppleVision project. It interfaces with the UR5e robot in Millrace.

## Setup

See [applevision_rospkg](https://github.com/OSURobotics/applevision_rospkg).

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
roslaunch millrace_moveit_config moveit_rviz.launch
```