# set minimum cmake version
cmake_minimum_required(VERSION 3.5 FATAL_ERROR)

# project name and language
project(recipe-02 LANGUAGES C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_EXTENSIONS OFF)
set(CMAKE_C_STANDARD_REQUIRED ON)

# Use modern Python3 module
find_package(Python3 COMPONENTS Interpreter Development REQUIRED)

# Print the found Python libraries and include directories
message(STATUS "Python3 include dir: ${Python3_INCLUDE_DIRS}")
message(STATUS "Python3 libraries: ${Python3_LIBRARIES}")

#find_package(PythonInterp REQUIRED)
#find_package(PythonLibs ${PYTHON_VERSION_MAJOR}.${PYTHON_VERSION_MINOR} EXACT REQUIRED)

add_executable(hello-embedded-python hello-embedded-python.c)

target_include_directories(hello-embedded-python
  PRIVATE
    ${Python3_INCLUDE_DIRS}
  )

target_link_libraries(hello-embedded-python
  PRIVATE
    ${Python3_LIBRARIES}
  )
