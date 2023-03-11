cmake_minimum_required (VERSION 3.11)

set(UNIT_TEST tests)
project(${UNIT_TEST})

enable_testing()

add_executable (${UNIT_TEST} "tests.cpp" "tests.h")
set(CMAKE_CXX_FLAGS_DEBUG_INIT "-Wall -g -Og")
set(CMAKE_CXX_FLAGS_RELEASE_INIT "-Wall -O3")

find_package(GTest CONFIG REQUIRED)
target_link_libraries(${UNIT_TEST} PRIVATE GTest::gtest GTest::gtest_main GTest::gmock GTest::gmock_main)

add_test(NAME test
         COMMAND test)

add_custom_command(
     TARGET ${UNIT_TEST}
     COMMENT "Run tests"
     POST_BUILD 
     COMMAND ${UNIT_TEST}
)