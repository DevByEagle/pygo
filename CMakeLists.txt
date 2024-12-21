cmake_minimum_required(VERSION 3.15)
project(Pythonic VERSION 1.0.0 LANGUAGES CXX)

file(GLOB LIBRARY_SOURCES "libs/*.cpp")

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

# Registers build options that are exposed to cmake
include(CMakeOptions.txt)

# Include CMake Modules
include(CompilerFlags)

add_executable(${PROJECT_NAME} src/main.cpp)

add_library(${PROJECT_NAME}42 SHARED ${LIBRARY_SOURCES})

set_target_properties(${PROJECT_NAME}42 PROPERTIES
    PREFIX ""
)

target_link_libraries(${PROJECT_NAME} ${PROJECT_NAME}42)