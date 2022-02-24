cmake_minimum_required(VERSION 3.5)

# Set the project name
project (third_party_include)


# find a boost install with the libraries filesystem and system
# This will search for CMake modules in the format "FindXXX.cmake" from the list of folders in CMAKE_MODULE_PATH
# On linux the default search path will include /usr/share/cmake/Modules
find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)
# 1.46.1 : The minimum version of boost to find
# REQUIRED : Tells the module that this is required and to fail it it cannot be found
# COMPONENTS : The list of libraries to find

# check if boost was found
if(Boost_FOUND)
    message ("boost found")
else()
    message (FATAL_ERROR "Cannot find Boost")
endif()

# Add an executable
add_executable(third_party_include main.cpp)

# link against the boost libraries
target_link_libraries( third_party_include
    PRIVATE
        Boost::filesystem
)

# message(STATUS ${Boost_INCLUDE_DIRS})