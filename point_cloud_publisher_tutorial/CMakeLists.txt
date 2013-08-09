cmake_minimum_required(VERSION 2.8.3)
project(point_cloud_publisher_tutorial)

find_package(catkin REQUIRED COMPONENTS sensor_msgs roscpp)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS})

# Build the executable
add_executable(point_cloud_publisher src/point_cloud_publisher.cpp)
# Add a build order dependency on sensor_msgs
# This ensures that sensor_msgs' msg headers are built before your executable
if(sensor_msgs_EXPORTED_TARGETS)
  add_dependencies(point_cloud_publisher ${sensor_msgs_EXPORTED_TARGETS})
endif()
# Link against the catkin libraries
target_link_libraries(point_cloud_publisher ${catkin_LIBRARIES})

# Install the executable
install(TARGETS point_cloud_publisher
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
