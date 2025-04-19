cmake_minimum_required(VERSION 3.10)

project(ctrl-c)

# if this is the top-level project and explicit install prefix not specified,
#  default to the install directory under the project root
if(PROJECT_IS_TOP_LEVEL AND CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
  set(CMAKE_INSTALL_PREFIX
    "${CMAKE_CURRENT_SOURCE_DIR}/install" CACHE PATH "" FORCE
  )
  message(STATUS "Explicit install prefix not specified; forcing ${CMAKE_INSTALL_PREFIX}")
endif()

add_subdirectory(src)

# if this is the top level project, also build the test subproject
if(PROJECT_IS_TOP_LEVEL)
  add_subdirectory(test)
endif()
