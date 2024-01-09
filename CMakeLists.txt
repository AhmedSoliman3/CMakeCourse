cmake_minimum_required(VERSION 3.16)
project(HELLOAPP VERSION 1.0)

# create source variable
set(SRC_FILES 
    main.cpp
    src/calc.cpp)

#print message 
message (STATUS "SRC Files have ${SRC_FILES}")

#print CMAKE_CXX_STANDARD
set(CMAKE_CXX_STANDARD 14) 
message (STATUS "Show C++ standard :${CMAKE_CXX_STANDARD}")

#print Env Path
message(STATUS "Path : $ENV{PATH}")

#Print CMAKE_SOURCE_DIR variable
message ("Path is ${CMAKE_SOURCE_DIR}")

#Print Project Paths
message ("Path is ${CMAKE_BINARY_DIR}")
message ("Path is ${CMAKE_SOURCE_DIR}")
message ("Path is ${CMAKE_CURRENT_BINARY_DIR}")
message ("Path is ${CMAKE_CURRENT_SOURCE_DIR}")

#If condition test
if(EXISTS ${CMAKE_SOURCE_DIR}/main.cpp)
    message("main.cpp exits")
else()
    message(FATAL_ERROR "main.cpp not exists")
endif()

# use source variable inside add_executable
add_executable(hellobinary ${SRC_FILES})
target_include_directories(hellobinary PUBLIC include/ lib/ ${PROJECT_BINARY_DIR})
# target_include_directories(hellobinary PRIVATE include/)

# Link wifi lib with the project 
add_subdirectory(${CMAKE_SOURCE_DIR}/lib)
target_link_libraries(hellobinary PUBLIC wifi_lib)

configure_file(defaultconfig.h.in defaultconfig.h)