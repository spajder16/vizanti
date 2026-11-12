cmake_minimum_required(VERSION 3.10)
project(vizanti_cpp)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(tf2_msgs REQUIRED)

add_executable(tf_consolidator src/tf_consolidator.cpp)
target_link_libraries(tf_consolidator
  rclcpp::rclcpp
  std_msgs::std_msgs__rosidl_typesupport_cpp
  tf2_msgs::tf2_msgs__rosidl_typesupport_cpp
)

install(TARGETS
  tf_consolidator
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
