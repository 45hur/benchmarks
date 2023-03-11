# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.11)

project ("Benchmarks")
include(./vcpkg/scripts/buildsystems/vcpkg.cmake)
find_package(benchmark REQUIRED)
find_package(GTest CONFIG REQUIRED)
# Include sub-projects.
add_subdirectory ("benchmarks")
add_subdirectory ("tests")