cmake_minimum_required(VERSION 3.13...3.19)

project(SW2Alg VERSION 0.1.0 LANGUAGES C)

set(CMAKE_C_STANDARD 11)

add_subdirectory(src)

# Use CTest to handle if enable_testing() should be used.
if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
    include(CTest)
endif()

if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME AND BUILD_TESTING)
    if(NOT EXISTS "${PROJECT_SOURCE_DIR}/extern/mtest/CMakeLists.txt")
        message(FATAL_ERROR "The submodules were not downloaded! GIT_SUBMODULE was turned off or failed. Please update submodules and try again.")
    else()
        add_subdirectory(extern/mtest)
    endif()
    add_subdirectory(test)
endif()
