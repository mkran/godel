cmake_minimum_required(VERSION 2.8.3)
project(godel_scan_analysis)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  pcl_ros
  roscpp
)

catkin_package(
  INCLUDE_DIRS include
  CATKIN_DEPENDS
    pcl_ros
    roscpp
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  include
)

add_executable(godel_scan_analysis_node 
  src/godel_scan_analysis_node.cpp
  src/scan_roughness_scoring.cpp
  src/keyence_scan_server.cpp
)

target_link_libraries(godel_scan_analysis_node
  ${catkin_LIBRARIES}
)

install(TARGETS godel_scan_analysis_node
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_GLOBAL_BIN_DESTINATION}
)
