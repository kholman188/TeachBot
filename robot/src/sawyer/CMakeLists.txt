cmake_minimum_required(VERSION 2.6)
project(sawyer)

find_package(catkin
  REQUIRED
  COMPONENTS
  rospy
  actionlib
  sensor_msgs
  control_msgs
  trajectory_msgs
  std_msgs
  cv_bridge
  dynamic_reconfigure
  intera_core_msgs
  intera_motion_msgs
  intera_interface
  genmsg
  message_generation
)

catkin_python_setup()

add_message_files(
  FILES
  adjustPoseTo.msg
  GoToJointAngles.msg
  JointInfo.msg
  joint_move.msg
  InteractionControl.msg
  JointImpedance.msg
  EndpointInfo.msg
  GoToCartesianPose.msg
  cuffInteraction.msg
  adjustPoseBy.msg
  Image.msg
)

generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs
)

#generate_dynamic_reconfigure_options(
#  cfg/SawyerJointSpringsExample.cfg
#)

catkin_package(
  CATKIN_DEPENDS
  rospy
  actionlib
  sensor_msgs
  control_msgs
  trajectory_msgs
  std_msgs
  cv_bridge
  dynamic_reconfigure
  intera_core_msgs
  intera_motion_msgs
  intera_interface
  message_runtime
  tf
  DEPENDS
  apriltag
)

install(
  DIRECTORY scripts/
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
  USE_SOURCE_PERMISSIONS
)

install(
  DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
  USE_SOURCE_PERMISSIONS
)

install(
  DIRECTORY share/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/share
  USE_SOURCE_PERMISSIONS
)
