# Minimum CMake version required
cmake_minimum_required(VERSION 3.10)

# Project name and version
project(Supernova VERSION 1.0)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Add include directories
include_directories(include)

# Add source files
file(GLOB_RECURSE SOURCES "src/*.cpp")

# Add static library
add_library(Supernova STATIC ${SOURCES})

# Find and include OpenGL
find_package(OpenGL REQUIRED)

# Find and include GLFW
find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)

# Include GLM directory (header-only, no linking needed)
find_path(GLM_INCLUDE_DIR glm/glm.hpp)
include_directories("/usr/include")



# Link the libraries
target_link_libraries(Supernova ${OPENGL_LIBRARIES} ${GLFW_LIBRARIES})
