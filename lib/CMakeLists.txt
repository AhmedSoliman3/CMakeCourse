cmake_minimum_required(VERSION 3.16)
message("Hello from lib")

message ("Path is ${CMAKE_BINARY_DIR}")
message ("Path is ${CMAKE_SOURCE_DIR}")
message ("Path is ${CMAKE_CURRENT_BINARY_DIR}")
message ("Path is ${CMAKE_CURRENT_SOURCE_DIR}")

add_library(wifi_lib
WIFI.cpp
WIFI.hpp)