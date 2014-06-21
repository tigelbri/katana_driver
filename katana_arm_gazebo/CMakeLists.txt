# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana_arm_gazebo)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS roscpp gazebo urdf xacro robot_state_publisher katana_description pr2_controller_manager robot_mechanism_controllers katana_gazebo_plugins katana_joint_movement_adapter actionlib pr2_controllers_msgs std_msgs)

include_directories(${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})

target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES} ${catkin_LIBRARIES})

add_executable(min_max_trajectory src/min_max_trajectory.cpp)

catkin_package(
    CATKIN_DEPENDS roscpp gazebo urdf xacro robot_state_publisher katana_description pr2_controller_manager robot_mechanism_controllers katana_gazebo_plugins katana_joint_movement_adapter actionlib pr2_controllers_msgs std_msgs
)
