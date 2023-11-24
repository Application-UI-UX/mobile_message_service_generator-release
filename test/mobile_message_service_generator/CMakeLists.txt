##############################################################################
# CMake
##############################################################################

cmake_minimum_required(VERSION 3.0.2)
project(genmobile)

##############################################################################
# Find Package
##############################################################################

find_package(catkin REQUIRED COMPONENTS genmsg rosmobile_build_tools)

##############################################################################
# Catkin
##############################################################################

catkin_package(
  CATKIN_DEPENDS genmsg rosmobile_build_tools
  CFG_EXTRAS
  genmobile-extras.cmake
  genmobile-catkin-api.cmake
)

catkin_python_setup()

##############################################################################
# Installs
##############################################################################

add_subdirectory(scripts)

file(WRITE ${CATKIN_DEVEL_PREFIX}/${GENMSG_LANGS_DESTINATION}/genmobile "Java")
install(
  FILES ${CATKIN_DEVEL_PREFIX}/${GENMSG_LANGS_DESTINATION}/genmobile
  DESTINATION ${GENMSG_LANGS_DESTINATION}
)

##############################################################################
# Tests
##############################################################################

#if(CATKIN_ENABLE_TESTING)
#  catkin_add_nosetests(test)
#endif()
