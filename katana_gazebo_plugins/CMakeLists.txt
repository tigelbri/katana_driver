# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(katana_gazebo_plugins)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS gazebo trajectory_msgs sensor_msgs object_manipulation_msgs control_toolbox actionlib katana_msgs pr2_controllers_msgs spline_smoother)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})

add_definitions(-fPIC)
add_library(gazebo_ros_katana_gripper src/gazebo_ros_katana_gripper.cpp src/katana_gripper_grasp_controller.cpp src/katana_gripper_joint_trajectory_controller.cpp src/gazebo_ros_katana_gripper_action_interface.cpp)

target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES} ${catkin_LIBRARIES})

add_executable(test_gripper_joint_trajectory src/test_gripper_joint_trajectory.cpp)

# catkin_package parameters: http://ros.org/doc/groovy/api/catkin/html/dev_guide/generated_cmake_api.html#catkin-package
catkin_package(
    CATKIN_DEPENDS gazebo trajectory_msgs sensor_msgs object_manipulation_msgs control_toolbox actionlib katana_msgs pr2_controllers_msgs spline_smoother
)
