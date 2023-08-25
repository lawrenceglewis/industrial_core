cmake_minimum_required(VERSION 3.5)

project(industrial_robot_simulator)

find_package(ament_cmake REQUIRED)

catkin_package()

##########
## Test ##
##########

if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
endif()

#############
## Install ##
#############

catkin_install_python(PROGRAMS ${PROJECT_NAME} DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

install(DIRECTORY launch/ DESTINATION share/${PROJECT_NAME}/launch)
