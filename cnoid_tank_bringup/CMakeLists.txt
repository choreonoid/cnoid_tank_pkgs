cmake_minimum_required(VERSION 3.5.0)
project(cnoid_tank_bringup)

find_package(catkin REQUIRED COMPONENTS
  choreonoid
  )

install(DIRECTORY
  model
  DESTINATION ${CHOREONOID_SHARE_SUBDIR}/cnoid_tank_bringup)
