cmake_minimum_required (VERSION 3.11)

project(bench)

add_executable (bench "benchmarks.cpp" "benchmarks.h")
set(CMAKE_CXX_FLAGS_DEBUG_INIT "-Wall -g -Og")
set(CMAKE_CXX_FLAGS_RELEASE_INIT "-Wall -O3")

find_package(benchmark CONFIG REQUIRED)
target_link_libraries(bench benchmark::benchmark benchmark::benchmark_main)

# Link Shlwapi to the project
if ("${CMAKE_SYSTEM_NAME}" MATCHES "Windows")
    target_link_libraries(bench Shlwapi)
endif()