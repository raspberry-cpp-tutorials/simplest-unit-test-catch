# src/CMakeLists.txt
cmake_minimum_required(VERSION 3.3 FATAL_ERROR)

# Project name and current version
project(anyproj VERSION 0.1 LANGUAGES CXX)

# Enable general warnings
# See http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

# Use 2017 C++ standard.
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Creates the compile_commands.json used by editors for code completion
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# To allow 'make test' and 'ctest' commands.
enable_testing()

# Find needed libraries:
find_package( OpenCV REQUIRED )

# compile the library:
add_library(anylib 
	cpp/orange-ball-detector
)

# Define headers for this library. When PUBLIC, headers used for
# compiling the library are also added to consumers' build
# paths (typically, the unit tests).
target_include_directories(anylib PUBLIC hpp)

# link to needed libraries
target_link_libraries(anylib
	${OpenCV_LIBS} 
	pthread
)

# Let's have unit tests:
add_subdirectory(tst)
