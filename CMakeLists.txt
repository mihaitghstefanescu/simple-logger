cmake_minimum_required (VERSION 2.8.11)
project (simple_logger)

add_library(simple_logger INTERFACE)

set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=gnu++11")

enable_testing ()
add_subdirectory (tests)

target_include_directories(simple_logger INTERFACE include/)
install(DIRECTORY include/
        DESTINATION include
        FILES_MATCHING
        PATTERN "*.hpp"
        PATTERN "*.h")
