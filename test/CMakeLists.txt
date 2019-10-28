cmake_minimum_required(VERSION 3.14)

project(MyProject)

add_subdirectory(.. ${CMAKE_BINARY_DIR}/GroupSourcesByFolder)

FILE(GLOB_RECURSE headers "${CMAKE_CURRENT_SOURCE_DIR}/*.h")
FILE(GLOB_RECURSE sources "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")

add_library(MyLibrary ${headers} ${sources})

GroupSourcesByFolder(MyLibrary)
