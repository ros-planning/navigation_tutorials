cmake_minimum_required(VERSION 2.8.3)
project(odometry_publisher_tutorial)

find_package(catkin REQUIRED COMPONENTS nav_msgs roscpp tf)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS})

# Build the executable
add_executable(odometry_publisher src/odometry_publisher.cpp)
# Add a build order dependency on nav_msgs
# This ensures that nav_msgs' msg headers are built before your executable
if(nav_msgs_EXPORTED_TARGETS)
  add_dependencies(odometry_publisher ${nav_msgs_EXPORTED_TARGETS})
endif()
# Link against the catkin libraries
target_link_libraries(odometry_publisher ${catkin_LIBRARIES})

# Install the executable
install(TARGETS odometry_publisher
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
