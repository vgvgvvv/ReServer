cmake_minimum_required(VERSION 3.10.0)

project(ReServer)

# ¸÷ÖÖdemo
add_subdirectory(demos)

include_directories(src)




############### Unit Test Start ###############

if (APPLE)
    add_definitions(-DGTEST_USE_OWN_TR1_TUPLE)
    add_definitions(-D__GLIBCXX__)
endif (APPLE)

# This adds another subdirectory, which has 'project(gtest)'.
add_subdirectory(libs/gtest-1.6.0)
enable_testing()

include_directories(${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})

##############
# Unit Tests
##############

file(GLOB_RECURSE test_src
        test/*.cpp)
add_executable(runUnitTests
        ${test_src})
target_link_libraries(runUnitTests gtest gtest_main)