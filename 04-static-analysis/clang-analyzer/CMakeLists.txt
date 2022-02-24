cmake_minimum_required (VERSION 3.5)

project(cppcheck_analysis)

# Use debug build as recommended
set(CMAKE_BUILD_TYPE Debug)

# Have cmake create a compile database
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Add sub directories
add_subdirectory(subproject1)
add_subdirectory(subproject2)


# sudo apt-get install clang-tools-7

# scan-build cmake ..
# scan-build make
# scan-view-7 /tmp/scan-build-2021-05-07-23-20-25-924589-skgi4a37