# src/tst/CMakeLists.txt

# test-config.h contains the path to the resources folder:
set(PATH_TO_TEST_DATA ${PROJECT_SOURCE_DIR}/tst/res)
configure_file (
	"test-config.h.in"
	"${PROJECT_BINARY_DIR}/test-config.h"
)

# Find needed libraries:
find_package( OpenCV REQUIRED )

# Creates a new executable to contain the tests:
add_executable(anytest
	main.cpp
	catch.hpp	

	orange-ball-detector-test
)

target_include_directories(anytest PRIVATE ${PROJECT_BINARY_DIR})

target_link_libraries(anytest 
	anylib
	${OpenCV_LIBS} 
	pthread
)

# Adds the executable to the test goal:
add_test(test anytest)