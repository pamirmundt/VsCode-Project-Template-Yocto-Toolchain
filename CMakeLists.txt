# CMakeLists.txt for the main project directory

# Set the minimum required CMake version
cmake_minimum_required(VERSION 3.12)

# Set the project name
project(VsCode-Project-Template-Yocto-Toolchain VERSION 0.1.0)

# Set the default build type to "Release" if not specified
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()

# Add compiler flags for debugging
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    add_compile_options(-g -O0)
endif()

# Set the output directory inside the main project directory
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

# Set executable name
set(EXECUTABLE_NAME helloWorld)

# Add the subdirectory for the source folder
add_subdirectory(src)

# Set any additional compiler flags
add_compile_options(-Wall -Wextra)

# Set any additional include directories
# include_directories(inc)

# Set any additional libraries
# target_link_libraries(${PROJECT_NAME} your_library)