cmake_minimum_required(VERSION 3.5)

project(hello_library)

############################################################
# Create a library
############################################################

#Generate the static library from the library sources
add_library(hello_library STATIC 
    src/Hello.cpp
)

target_include_directories(hello_library
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include
)
# PRIVATE - the directory is added to this target’s include directories
# INTERFACE - the directory is added to the include directories for any targets that link this library.
# PUBLIC - As above, it is included in this library and also any targets that link this library.


############################################################
# Create an executable
############################################################

# Add an executable with the above sources
add_executable(hello_binary 
    src/main.cpp
)

# link the new hello_library target with the hello_binary target
target_link_libraries( hello_binary
    PRIVATE 
        hello_library
        # NOTE: not ${hello_library}
)
