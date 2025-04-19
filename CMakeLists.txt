cmake_minimum_required(VERSION 3.10)
project(ctrl-c)
if(PROJECT_IS_TOP_LEVEL AND CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
  set(CMAKE_INSTALL_PREFIX
    "${CMAKE_CURRENT_SOURCE_DIR}/install" CACHE PATH "" FORCE
  )
  message(STATUS "Explicit install prefix not specified; forcing ${CMAKE_INSTALL_PREFIX}")
endif()
add_subdirectory(src)
