cmake_minimum_required(VERSION 3.0.2)
project(agm_comm)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  actionlib
  agm_msgs
  roscpp
  rospy
  std_msgs
  move_base_msgs
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  move_base_msgs   std_msgs agm_msgs
)

catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES agm_comm
#  CATKIN_DEPENDS agm_msgs roscpp rospy std_msgs
#  DEPENDS system_lib
)

include_directories(
# include
  ${catkin_INCLUDE_DIRS}
)

add_executable(agm_worker_node src/agm_worker_node.cpp)
target_link_libraries(agm_worker_node ${catkin_LIBRARIES})

add_executable(web_comm_server_node src/web_comm_server_node.cpp)
target_link_libraries(web_comm_server_node ${catkin_LIBRARIES} curl)

