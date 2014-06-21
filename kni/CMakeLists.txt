# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(kni)
# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED )

execute_process(COMMAND cmake -E chdir ${PROJECT_SOURCE_DIR}/KNI_4.3.0/src/common/ make
                RESULT_VARIABLE _make_failed)
if(_make_failed)
  message(FATAL_ERROR "Build of common files failed")
endif(_make_failed)

execute_process(COMMAND cmake -E chdir ${PROJECT_SOURCE_DIR}/KNI_4.3.0/src/Base/ make
                RESULT_VARIABLE _make_failed)
if(_make_failed)
  message(FATAL_ERROR "Build of Base library failed")
endif(_make_failed)

execute_process(COMMAND cmake -E chdir ${PROJECT_SOURCE_DIR}/KNI_4.3.0/lib/kinematics/roboop/ make
                RESULT_VARIABLE _make_failed)
if(_make_failed)
  message(FATAL_ERROR "Build of roboop library failed")
endif(_make_failed)

execute_process(COMMAND cmake -E chdir ${PROJECT_SOURCE_DIR}/KNI_4.3.0/lib/kinematics/ make
                RESULT_VARIABLE _make_failed)
if(_make_failed)
  message(FATAL_ERROR "Build of kinematics library failed")
endif(_make_failed)

execute_process(COMMAND cmake -E chdir ${PROJECT_SOURCE_DIR}/KNI_4.3.0/src/InvKin/ make
                RESULT_VARIABLE _make_failed)
if(_make_failed)
  message(FATAL_ERROR "Build of InvKin library failed")
endif(_make_failed)

execute_process(COMMAND cmake -E chdir ${PROJECT_SOURCE_DIR}/KNI_4.3.0/src/LM/ make
                RESULT_VARIABLE _make_failed)
if(_make_failed)
  message(FATAL_ERROR "Build of LM library failed")
endif(_make_failed)

# catkin_package parameters: http://ros.org/doc/groovy/api/catkin/html/dev_guide/generated_cmake_api.html#catkin-package
catkin_package()
