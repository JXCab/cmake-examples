# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.5)

# Set a default build type if none was specified
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message("Setting build type to 'RelWithDebInfo' as none was specified.")
  set(CMAKE_BUILD_TYPE RelWithDebInfo CACHE STRING "Choose the type of build." FORCE)
  # Set the possible values of build type for cmake-gui
  # 当使用cmake-gui的时候，设置构建级别的四个可选项
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release"
    "MinSizeRel" "RelWithDebInfo")
endif()

# Set the project name
project (build_type)

# Add an executable
add_executable(cmake_examples_build_type main.cpp)


# cmake .. -DCMAKE_BUILD_TYPE=Release
# cmake .. -DCMAKE_BUILD_TYPE=Debug
# cmake .. -DCMAKE_BUILD_TYPE=MinSizeRel
# cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo

# make VERBOSE=1

# Release - Adds the -O3 -DNDEBUG flags to the compiler.  不可以打断点调试，程序开发完成后发行使用的版本，占的体积小。 它对代码做了优化，因此速度会非常快
# Debug - Adds the -g flag.  调试的版本，体积大。
# MinSizeRel - Adds -Os -DNDEBUG  最小体积版本
# RelWithDebInfo - Adds -O2 -g -DNDEBUG flags.  既优化又能调试

# set 设置的变量值 作用域属于整个 CMakeLists.txt 文件。(一个工程可能有多个CMakeLists.txt)