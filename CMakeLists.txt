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

enable_testing()

find_package(GTest CONFIG REQUIRED)

add_executable(test_concaveman
  src/test/cpp/test_concaveman.cpp)
target_compile_features(test_concaveman PRIVATE cxx_std_20)
target_link_libraries(test_concaveman PRIVATE
  concaveman-cpp
  GTest::gtest_main
)
add_test(NAME test_concaveman COMMAND test_concaveman)
