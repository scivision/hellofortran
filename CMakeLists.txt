cmake_minimum_required(VERSION 3.14...${CMAKE_VERSION})

project(child LANGUAGES Fortran)

add_library(times_two times_two.f90)
target_include_directories(times_two INTERFACE ${CMAKE_CURRENT_BINARY_DIR}/include)
set_target_properties(times_two PROPERTIES
  Fortran_MODULE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/include)

if(CMAKE_VERSION VERSION_GREATER_EQUAL 3.21)
  if(PROJECT_IS_TOP_LEVEL)
    message(STATUS "${PROJECT_NAME} is the top-level project")
  else()
    message(STATUS "${PROJECT_NAME} is an external project")
  endif()
endif()
