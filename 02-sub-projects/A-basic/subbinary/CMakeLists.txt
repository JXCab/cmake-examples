project(subbinary)

# Create the executable
add_executable(${PROJECT_NAME} main.cpp)

# Link the static library from subproject1 using it's alias sub::lib1
# Link the header only library from subproject2 using it's alias sub::lib2
# This will cause the include directories for that target to be added to this project
target_link_libraries(${PROJECT_NAME}
    sub::lib1
    sub::lib2
)

#  这里不需要添加头文件
#   When adding the libraries from the sub-projects, starting from cmake v3,
# there is no need to add the projects include directories in the include
# directories of the binary using them.


# PROJECT_NAME : The name of the project set by the current project()
# CMAKE_PROJECT_NAME : the name of the first project set by the project() command, i.e. the top level project
# PROJECT_SOURCE_DIR : The source director of the current project
# PROJECT_BINARY_DIR : The build directory for the current project
