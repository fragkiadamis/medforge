# Set the minimum required version of CMake
cmake_minimum_required(VERSION 3.28.3)

# Set the project name and version
project(medforge VERSION 0.1)

# Include directories for project header files
include_directories(include)

# Define directories for headers and source files in the project
set(HEADERS_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include")
set(SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src")

# Gather all header (.h) and source (.cxx) files recursively in the respective directories
file(GLOB_RECURSE HEADER_FILES "${HEADERS_DIR}/*.h" SOURCE_FILES "${SOURCE_DIR}/*.cxx")

# Add the executable
add_executable(
    ${PROJECT_NAME}
    ${HEADER_FILES}
    ${SOURCE_FILES}
)

# Define the MEDFORMATTOOLS_VERSION macro to use in the code
target_compile_definitions(${PROJECT_NAME} PRIVATE ${PROJECT_NAME}_VERSION="${PROJECT_VERSION}")
