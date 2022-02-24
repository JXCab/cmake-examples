cmake_minimum_required(VERSION 3.5)

# Set the project name
project (protobuf_example)

# find the protobuf compiler and libraries
find_package(Protobuf REQUIRED)

# check if protobuf was found
# PROTOBUF_FOUND: If Protocol Buffers is installed
if(PROTOBUF_FOUND)
    message ("protobuf found")
else()
    message (FATAL_ERROR "Cannot find Protobuf")
endif()

# Generate the .h and .cxx files
# PROTO_SRCS : Name of the variable that will store the .pb.cc files
# PROTO_HDRS : Name of the variable that will store the .pb.h files
# AddressBook.proto : The .proto file to generate code from
# After the PROTOBUF_GENERATE_CPP function is called, you will have the above mentioned variables available !!!
PROTOBUF_GENERATE_CPP(PROTO_SRCS PROTO_HDRS AddressBook.proto)

# Print path to generated files
message ("PROTO_SRCS = ${PROTO_SRCS}")
message ("PROTO_HDRS = ${PROTO_HDRS}")

# Add an executable
add_executable(protobuf_example
    main.cpp
    ${PROTO_SRCS}
    ${PROTO_HDRS})

# PROTOBUF_INCLUDE_DIRS : The protobuf header files
target_include_directories(protobuf_example
    PUBLIC
    ${PROTOBUF_INCLUDE_DIRS}
    ${CMAKE_CURRENT_BINARY_DIR}  # 为什么加这行 ？？？ 
)

# link the exe against the libraries
# PROTOBUF_LIBRARIES : The protobuf library
target_link_libraries(protobuf_example
    PUBLIC
    ${PROTOBUF_LIBRARIES}
)
