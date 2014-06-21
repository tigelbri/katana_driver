# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana_arm_gazebo)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS roscpp gazebo_ros urdf xacro robot_state_publisher katana_description pr2_controller_manager robot_mechanism_controllers katana_gazebo_plugins joint_trajectory_controller actionlib pr2_controllers_msgs std_msgs)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})
include(FindPkgConfig)
if(PKG_CONFIG_FOUND)
   pkg_check_modules(GAZEBO gazebo)
endif()

# catkin_package parameters: http://ros.org/doc/groovy/api/catkin/html/dev_guide/generated_cmake_api.html#catkin-package
catkin_package(
    CATKIN_DEPENDS roscpp gazebo_ros urdf xacro robot_state_publisher katana_description pr2_controller_manager robot_mechanism_controllers katana_gazebo_plugins joint_trajectory_controller actionlib pr2_controllers_msgs std_msgs
)

include_directories(${GAZEBO_INCLUDE_DIRS})
link_directories(${GAZEBO_LIBRARY_DIRS})

add_executable(min_max_trajectory src/min_max_trajectory.cpp)
target_link_libraries(min_max_trajectory ${GAZEBO_LIBRARIES} ${catkin_LIBRARIES})


