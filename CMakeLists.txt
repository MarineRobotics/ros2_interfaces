cmake_minimum_required(VERSION 3.5)
project(mr_interfaces)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)

find_package(builtin_interfaces REQUIRED)

find_package(rosidl_default_generators REQUIRED)

set(srv_files
  "srv/ReadGPIO.srv"
  "srv/SetGPIO.srv"
  "srv/StateRequest.srv"
)

set(msg_files
  "msg/ADCReading.msg"
  "msg/Declination.msg"
  "msg/Depth.msg"
  "msg/DigitalReading.msg"
  "msg/GNSSData.msg"
  "msg/Heading.msg"
  "msg/Humidity.msg"
  "msg/LCD.msg"
  "msg/N2KInfo.msg"
  "msg/NetworkInfo.msg"
  "msg/NetworkInterface.msg"
  "msg/NodeStatus.msg"
  "msg/PID.msg"
  "msg/Position.msg"
  "msg/Pressure.msg"
  "msg/RoboclawStatus.msg"
  "msg/ROT.msg"
  "msg/Speed.msg"
  "msg/Temp.msg"
  "msg/Wind.msg"
)

set (action_files
  "action/GPIO.action"
  "action/SetPeripheral.action"
  "action/Sleep.action"
  "action/TogglePeripheral.action"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
  ${action_files}
  DEPENDENCIES builtin_interfaces
)

install(
  FILES mr_mapping_rules.yaml
  DESTINATION share/${PROJECT_NAME})

ament_export_dependencies(rosidl_default_runtime)

ament_package()
