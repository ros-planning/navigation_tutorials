cmake_minimum_required(VERSION 2.8.3)
project(simple_navigation_goals_tutorial)

find_package(catkin REQUIRED COMPONENTS actionlib move_base_msgs roscpp tf)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS})

# Build the executable
add_executable(simple_navigation_goals src/simple_navigation_goals.cpp)
# Add a build order dependency on nav_msgs
# This ensures that all msg headers are built before your executable
if(catkin_EXPORTED_TARGETS)
  add_dependencies(simple_navigation_goals ${catkin_EXPORTED_TARGETS})
endif()
# Link against the catkin libraries
target_link_libraries(simple_navigation_goals ${catkin_LIBRARIES})

# Install the executable
install(TARGETS simple_navigation_goals
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
