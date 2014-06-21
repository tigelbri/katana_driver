# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS roscpp roslib kni geometry_msgs std_srvs sensor_msgs actionlib pr2_controllers_msgs control_msgs trajectory_msgs urdf tf katana_msgs moveit_msgs armadillo)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})

# catkin_package parameters: http://ros.org/doc/groovy/api/catkin/html/dev_guide/generated_cmake_api.html#catkin-package
catkin_package(
    CATKIN_DEPENDS roscpp roslib kni geometry_msgs std_srvs sensor_msgs actionlib pr2_controllers_msgs control_msgs trajectory_msgs urdf tf katana_msgs moveit_msgs armadillo
)

add_executable(katana src/KatanaNode.cpp src/AbstractKatana.cpp src/Katana.cpp src/Katana300.cpp src/SimulatedKatana.cpp src/JointStatePublisher.cpp src/joint_trajectory_action_controller.cpp src/joint_movement_action_controller.cpp src/KNIConverter.cpp src/spline_functions.cpp src/katana_gripper_grasp_controller.cpp)
add_executable(katana_arm_kinematics src/KNIConverter.cpp src/KNIKinematics.cpp)
