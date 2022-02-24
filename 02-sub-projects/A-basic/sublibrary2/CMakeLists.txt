# Set the project name
project (sublibrary2)

#   Header only library
#   If you have a library that is created as a header only library,
# cmake supports the INTERFACE target to allow creating a target without any build output. 
add_library(${PROJECT_NAME} INTERFACE)
add_library(sub::lib2 ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    INTERFACE
        ${PROJECT_SOURCE_DIR}/include
)
