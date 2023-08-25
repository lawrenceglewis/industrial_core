cmake_minimum_required(VERSION 3.5)

project(industrial_msgs)

#find_package(catkin REQUIRED COMPONENTS message_generation std_msgs trajectory_msgs) not sure if i need message_generation or not.

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)

ament_export_dependencies(message_runtime)
ament_export_dependencies(std_msgs)
ament_export_dependencies(trajectory_msgs)

ament_package()
