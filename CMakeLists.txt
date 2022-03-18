cmake_minimum_required(VERSION 3.4)
project(millrace_moveit_config)

find_package(catkin REQUIRED)

catkin_package()

install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
