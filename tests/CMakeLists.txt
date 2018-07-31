# For now, Google Test is NOT required */
find_package(GTest)

# If not found, print a status message and return
if(NOT GTEST_FOUND)
    message(STATUS "Install Google Test to enable additional unit testing")
    return ()
endif()

# Unit tests - logger header library
add_executable(logger_tests logger_tests.cxx)
target_link_libraries(logger_tests pthread GTest::GTest GTest::Main)
target_include_directories(logger_tests PRIVATE "../include/")
gtest_add_tests(logger_tests "" AUTO)

# Add a custom target for unit tests
add_custom_target(tests-unit ALL
    DEPENDS
    logger_tests
    COMMENT "UPM unit test collection")

