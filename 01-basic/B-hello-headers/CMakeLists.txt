# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)

# Set the project name
project (hello_headers)

# Create a sources **variable** with a link to all cpp files to compile
set(SOURCES
    src/Hello.cpp
    src/main.cpp
)
# file(GLOB SOURCES "src/*.cpp")

# Add an executable with the above sources
add_executable(hello_headers ${SOURCES})

# Set the directories that should be included in the build command for this target
# when running g++ these will be included as -I/directory/path/
target_include_directories(hello_headers
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
        # ${CMAKE_CURRENT_SOURCE_DIR}/include  # 或者这样
)

# WHY PRIVATE ?

# CMAKE_SOURCE_DIR : The root source directory
# CMAKE_CURRENT_SOURCE_DIR : The current source directory if using sub-projects and directories
# PROJECT_SOURCE_DIR : The source directory of the current cmake project
# CMAKE_BINARY_DIR : The root binary / build directory. This is the directory where you ran the cmake command
# CMAKE_CURRENT_BINARY_DIR : The build directory you are currently in
# PROJECT_BINARY_DIR : The build directory for the current project


# make VERBOSE=1  see the full output for debugging purposes
