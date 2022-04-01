cmake_minimum_required(VERSION 3.4)
project(millrace_moveit_config)

find_package(catkin REQUIRED COMPONENTS roslaunch)

catkin_package()

roslaunch_add_file_check(launch)

install(DIRECTORY config launch meshes urdf DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})