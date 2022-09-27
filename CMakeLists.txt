cmake_minimum_required(VERSION 3.0.2)
project(robotiq_simple_driver)

find_package(catkin REQUIRED COMPONENTS message_generation actionlib_msgs)

add_action_files(
  DIRECTORY
  action
  FILES
  MoveGripper.action
)

generate_messages(DEPENDENCIES actionlib_msgs)

catkin_package(
  CATKIN_DEPENDS message_runtime actionlib_msgs
)

catkin_install_python(
  PROGRAMS nodes/gripper_server
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
