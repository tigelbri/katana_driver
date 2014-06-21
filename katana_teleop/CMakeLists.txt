# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana_teleop)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS control_msgs sensor_msgs roscpp katana_msgs actionlib)

catkin_package(
    CATKIN_DEPENDS control_msgs sensor_msgs roscpp katana_msgs actionlib
)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES} ${catkin_LIBRARIES})
add_executable(katana_teleop_key src/katana_teleop_key.cpp) 
