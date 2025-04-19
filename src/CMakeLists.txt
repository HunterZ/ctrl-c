add_library(ctrl-c STATIC)
target_sources(ctrl-c
  PRIVATE ctrl-c.cpp
  PUBLIC FILE_SET HEADERS
  BASE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}
  FILES ctrl-c.h
)
include(CMakePackageConfigHelpers)
include(GNUInstallDirs)
install(TARGETS ctrl-c
  EXPORT ctrl-cTargets
  FILE_SET HEADERS
)
# Allow package maintainers to freely override the path for the configs
set(ctrl-c_INSTALL_CMAKEDIR
  "${CMAKE_INSTALL_LIBDIR}/cmake/ctrl-c"
  CACHE PATH "CMake package config location relative to the install prefix"
)
mark_as_advanced(ctrl-c_INSTALL_CMAKEDIR)
install(EXPORT ctrl-cTargets
  FILE ctrl-cTargets.cmake
  DESTINATION "${ctrl-c_INSTALL_CMAKEDIR}"
)
configure_package_config_file("${PROJECT_SOURCE_DIR}/cmake/Config.cmake.in"
  "${CMAKE_CURRENT_BINARY_DIR}/ctrl-cConfig.cmake"
  INSTALL_DESTINATION "${ctrl-c_INSTALL_CMAKEDIR}"
  NO_SET_AND_CHECK_MACRO
  NO_CHECK_REQUIRED_COMPONENTS_MACRO
)
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/ctrl-cConfig.cmake"
  DESTINATION "${ctrl-c_INSTALL_CMAKEDIR}"
)
