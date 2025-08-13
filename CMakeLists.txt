cmake_minimum_required(VERSION 3.30)

project(concaveman-cpp LANGUAGES CXX)

add_library(concaveman-cpp INTERFACE)
target_sources(
  concaveman-cpp
  PUBLIC
  FILE_SET HEADERS
  BASE_DIRS src/main/cpp/include
  FILES
  src/main/cpp/include/concaveman-cpp/concaveman.h
)

add_executable(test_concaveman
  src/test/cpp/test_concaveman.cpp)
target_link_libraries(test_concaveman PRIVATE
  concaveman-cpp
)