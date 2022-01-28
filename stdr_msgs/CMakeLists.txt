cmake_minimum_required(VERSION 3.5)
project(stdr_msgs)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(actionlib_msgs REQUIRED)

set(msg_files
  "msg/Noise.msg"
  "msg/LaserSensorMsg.msg"
  "msg/SonarSensorMsg.msg"
  "msg/KinematicMsg.msg"
  "msg/FootprintMsg.msg"
  "msg/RobotMsg.msg"
  "msg/RobotIndexedMsg.msg"
  "msg/RobotIndexedVectorMsg.msg"

  "msg/RfidSensorMsg.msg"
  "msg/RfidSensorMeasurementMsg.msg"
  "msg/RfidTag.msg"
  "msg/RfidTagVector.msg"

  "msg/SoundSensorMsg.msg"
  "msg/SoundSensorMeasurementMsg.msg"
  "msg/SoundSource.msg"
  "msg/SoundSourceVector.msg"

  "msg/ThermalSensorMsg.msg"
  "msg/ThermalSensorMeasurementMsg.msg"
  "msg/ThermalSource.msg"
  "msg/ThermalSourceVector.msg"

  "msg/CO2SensorMsg.msg"
  "msg/CO2SensorMeasurementMsg.msg"
  "msg/CO2Source.msg"
  "msg/CO2SourceVector.msg"

  "srv/LoadMap.srv"
  "srv/LoadExternalMap.srv"
  "srv/RegisterGui.srv"
  "srv/MoveRobot.srv"

  "srv/AddRfidTag.srv"
  "srv/DeleteRfidTag.srv"

  "srv/AddThermalSource.srv"
  "srv/DeleteThermalSource.srv"

  "srv/AddSoundSource.srv"
  "srv/DeleteSoundSource.srv"

  "srv/AddCO2Source.srv"
  "srv/DeleteCO2Source.srv"

  "action/RegisterRobot.action"
  "action/SpawnRobot.action"
  "action/DeleteRobot.action"
)
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES std_msgs
  geometry_msgs
  actionlib_msgs
  nav_msgs
  actionlib_msgs
  )

ament_export_dependencies(rosidl_default_runtime)

ament_package()

