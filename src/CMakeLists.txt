# Add all the source files in the current directory to the project
file(GLOB_RECURSE SOURCES "*.cpp" "*.c")

# Add the executable target
add_executable(${EXECUTABLE_NAME} ${SOURCES})

# Set any additional include directories
target_include_directories(${EXECUTABLE_NAME} PRIVATE ${PROJECT_SOURCE_DIR}/inc)