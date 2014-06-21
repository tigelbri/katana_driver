# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana_msgs)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS sensor_msgs actionlib_msgs)

#include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})

include(${actionlib_msgs_PACKAGE_PATH}/cmake/actionbuild.cmake)
genaction()

catkin_package(
    CATKIN_DEPENDS sensor_msgs actionlib_msgs
)
