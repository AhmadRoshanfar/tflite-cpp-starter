cmake_minimum_required(VERSION 3.17)
project(Minimal)

set(CMAKE_CXX_STANDARD 14)

# include has 2 subdirectories: tensorflow and flatbuffers
# INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/tflite-dist/include/)

# lib has 1 file: libtensorflowlite.so

ADD_LIBRARY(tensorflowlite SHARED IMPORTED)
set_property(TARGET tensorflowlite PROPERTY IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/libs/libtensorflowlite.so)

add_executable(Minimal main.cpp)
target_link_libraries(Minimal tensorflowlite)