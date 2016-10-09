############################################
#
# libcdsl uses cmake because it's simple
#   Build instructions can be found in the README
#
############################################

# Set some flags
cmake_minimum_required(VERSION 2.8.11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c11")
set(CMAKE_BUILD_TYPE Debug)

# Create our project for further reference
project(libcthpool)

set(CTHPOOL_SRC thpool.c)

# Define our library in cmake
add_library(libcthpool STATIC ${CTHPOOL_SRC})

# Dynamically linked libraries
target_link_libraries(libcthpool pthread)

# Include the subdirectories to search for headers
target_include_directories(libcthpool PUBLIC ".")

# since the name starts with 'lib' dont add it again
set_target_properties(libcthpool PROPERTIES PREFIX "")
