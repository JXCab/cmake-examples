cmake_minimum_required(VERSION 3.5)

project(cmake_examples_install)

############################################################
# Create a library
############################################################

#Generate the shared library from the library sources
add_library(cmake_examples_inst SHARED
    src/Hello.cpp
)

target_include_directories(cmake_examples_inst
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include
)

############################################################
# Create an executable
############################################################

# Add an executable with the above sources
add_executable(cmake_examples_inst_bin
    src/main.cpp
)

# link the new hello_library target with the hello_binary target
target_link_libraries( cmake_examples_inst_bin
    PRIVATE 
        cmake_examples_inst
)

############################################################
# Install
############################################################

# CMake offers the ability to add a make install target to allow a user to install binaries, libraries and other files. 
# The base install location is controlled by the variable CMAKE_INSTALL_PREFIX
# which can be set using ccmake or by calling cmake with cmake .. -DCMAKE_INSTALL_PREFIX=/install/location

#   ${CMAKE_BINARY_DIR}:
# /media/rvb0032/0A9AD66165F33762/cmake-examples/01-basic/E-installing/build/

if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    message(STATUS "Setting default CMAKE_INSTALL_PREFIX path to ${CMAKE_BINARY_DIR}/install")
    set(CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}/install" CACHE STRING "The path to use for make install" FORCE)
endif()

# the default install location is set from the CMAKE_INSTALL_PERFIX, which defaults to /usr/local/
# cmake .. -DCMAKE_INSTALL_PREFIX=/media/rvb0032/0A9AD66165F33762/jx.cai/cmake/cmake-examples/01-basic/E-installing/install
# 更改 install 目录, 可以由上述的方法, 也可以在 cmake 时指定


# Binaries
# Install the binary generated from the target cmake_examples_inst_bin target to the destination ${CMAKE_INSTALL_PREFIX}/bin
install (TARGETS cmake_examples_inst_bin
    DESTINATION bin)

# Library
# Note: may not work on windows
# Install the shared library generated from the target cmake_examples_inst target to the destination ${CMAKE_INSTALL_PREFIX}/lib
install (TARGETS cmake_examples_inst
    LIBRARY DESTINATION lib)

# Header files
# Install the header files for developing against the cmake_examples_inst library into the ${CMAKE_INSTALL_PREFIX}/include directory
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/ 
    DESTINATION include)

# Config
# Install a configuration file to the destination ${CMAKE_INSTALL_PREFIX}/etc
install (FILES cmake-examples.conf
    DESTINATION etc)



