cmake_minimum_required(VERSION 3.5)
project(tello_interfaces)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(std_msgs REQUIRED)

# Generate interfaces
rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Object.msg"
  "msg/DroneStatus.msg"
  "msg/TargetInfo.msg"
  "msg/LocalPose.msg"
  "msg/DroneAction.msg"
  DEPENDENCIES geometry_msgs std_msgs
)

ament_package()