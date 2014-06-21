# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana_tutorials)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS roscpp actionlib trajectory_msgs control_msgs pr2_controllers_msgs sensor_msgs)

catkin_package(
    CATKIN_DEPENDS roscpp actionlib trajectory_msgs control_msgs pr2_controllers_msgs sensor_msgs
)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES} ${catkin_LIBRARIES})

add_executable(follow_joint_trajectory_client src/follow_joint_trajectory_client.cpp)
add_executable(pr2_joint_trajectory_client src/pr2_joint_trajectory_client.cpp)

