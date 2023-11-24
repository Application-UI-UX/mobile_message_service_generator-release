cmake_minimum_required(VERSION 3.8)
project(mobile_message_service_generator)


# Find ROS
if($ENV{ROS_VERSION} EQUAL 1)
  find_package(
    catkin REQUIRED COMPONENTS 
    genmsg
    mobile_catkin_gradle_plugins
    mobile_catkin_modules_build_development_tools
    )
else()
  find_package(ament_cmake REQUIRED
    genmsg
    mobile_catkin_gradle_plugins
    mobile_catkin_modules_build_development_tools
    )
endif()


if($ENV{ROS_VERSION} EQUAL 1)
  catkin_package(
    CATKIN_DEPENDS genmsg mobile_catkin_modules_build_development_tools
    CFG_EXTRAS
    mobile_message_service_generator-extras.cmake
    mobile_message_service_generator-catkin-api.cmake
  )
endif()

catkin_python_setup()

add_subdirectory(scripts)

file(WRITE ${CATKIN_DEVEL_PREFIX}/${GENMSG_LANGS_DESTINATION}/mobile_message_service_generator "Java")
install(
  FILES ${CATKIN_DEVEL_PREFIX}/${GENMSG_LANGS_DESTINATION}/mobile_message_service_generator
  DESTINATION ${GENMSG_LANGS_DESTINATION}
)
