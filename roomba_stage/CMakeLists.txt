cmake_minimum_required(VERSION 2.8.3)
project(roomba_stage)

# Find catkin
find_package(catkin REQUIRED)

catkin_package()

# Install maps files
install(DIRECTORY maps
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

# Install params files
install(DIRECTORY params
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

# Install other files
install(FILES move_base_lse_arena.launch roomba_lse_arena.world roomba_stage.rviz
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
