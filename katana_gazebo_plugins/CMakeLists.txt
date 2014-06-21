# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana_gazebo_plugins)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS gazebo_ros trajectory_msgs sensor_msgs control_toolbox actionlib katana_msgs pr2_controllers_msgs control_msgs)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})

add_definitions(-fPIC)

include(FindPkgConfig)
if(PKG_CONFIG_FOUND)
   pkg_check_modules(GAZEBO gazebo)
endif()

include_directories(${GAZEBO_INCLUDE_DIRS})
link_directories(${GAZEBO_LIBRARY_DIRS})

catkin_package(
    CATKIN_DEPENDS gazebo_ros trajectory_msgs sensor_msgs control_toolbox actionlib katana_msgs pr2_controllers_msgs control_msgs
)

add_library(gazebo_ros_katana_gripper src/gazebo_ros_katana_gripper.cpp src/katana_gripper_grasp_controller.cpp src/katana_gripper_joint_trajectory_controller.cpp src/gazebo_ros_katana_gripper_action_interface.cpp)
target_link_libraries(gazebo_ros_katana_gripper ${GAZEBO_libraries} ${catkin_libraries})

add_executable(test_gripper_joint_trajectory src/test_gripper_joint_trajectory.cpp)
