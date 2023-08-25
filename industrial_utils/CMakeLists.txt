cmake_minimum_required(VERSION 3.5)

project(industrial_utils)

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)

find_package(Boost REQUIRED)
find_package(system REQUIRED)

catkin_package(
    CATKIN_DEPENDS roscpp urdf
    INCLUDE_DIRS include
    LIBRARIES ${PROJECT_NAME}
)
ament_export_dependencies(urdf)
ament_export_include_directories(include)
ament_export_libraries(${PROJECT_NAME})

include_directories(include)

add_library(${PROJECT_NAME} src/param_utils.cpp src/utils.cpp)
ament_target_dependencies(${PROJECT_NAME} ${catkin_LIBRARIES})



if(BUILD_TESTING)
    ament_add_gtest(utest_inds_utils test/utest.cpp)
    ament_target_dependencies(utest_inds_utils ${PROJECT_NAME} ${catkin_LIBRARIES})
endif()


install(
    TARGETS ${PROJECT_NAME} 
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
    RUNTIME DESTINATION lib/${PROJECT_NAME})

install(
    DIRECTORY include/${PROJECT_NAME}/
    DESTINATION include/${PROJECT_NAME})

ament_package()