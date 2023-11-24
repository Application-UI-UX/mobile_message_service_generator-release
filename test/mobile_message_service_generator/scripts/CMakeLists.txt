##############################################################################
# Installs
##############################################################################

# Rosrunnable installation of scripts
catkin_install_python(
  PROGRAMS
  genmobile_gradle_project.py
  genmobile_message_artifacts
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
