cmake_minimum_required(VERSION 2.8.3)
project(robot_setup_tf_tutorial)

find_package(catkin REQUIRED COMPONENTS geometry_msgs roscpp tf)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS})

# Build the tf_broadcaster executable
add_executable(tf_broadcaster src/tf_broadcaster.cpp)
# Add a build order dependency on geometry_msgs
# This ensures that geometry_msgs' msg headers are built before your executable
if(geometry_msgs_EXPORTED_TARGETS)
  add_dependencies(tf_broadcaster ${geometry_msgs_EXPORTED_TARGETS})
endif()
# Link against the catkin libraries
target_link_libraries(tf_broadcaster ${catkin_LIBRARIES})

# Build the tf_listener executable
add_executable(tf_listener src/tf_listener.cpp)
# Add a build order dependency on geometry_msgs
# This ensures that geometry_msgs' msg headers are built before your executable
if(geometry_msgs_EXPORTED_TARGETS)
  add_dependencies(tf_listener ${geometry_msgs_EXPORTED_TARGETS})
endif()
# Link against the catkin libraries
target_link_libraries(tf_listener ${catkin_LIBRARIES})

# Install the executable
install(TARGETS tf_broadcaster tf_listener
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
