cmake_minimum_required(VERSION 3.17)
project(cmake_toolchain_var_bug)

set(CMAKE_CXX_STANDARD 11)

if(NOT DEFINED CMAKE_TOOLCHAIN_FILE)
    message(FATAL_ERROR "Please specify a toolchain file with -DCMAKE_TOOLCHAIN_FILE=")
endif()

message(STATUS "CMAKE_TOOLCHAIN_FILE=${CMAKE_TOOLCHAIN_FILE}")

if(IS_ABSOLUTE ${CMAKE_TOOLCHAIN_FILE})
    message(STATUS "Toolchain file path is absolute")
else()
    message(WARNING "Toolchain file path is NOT absolute")
endif()

include(Workaround.cmake)
message(STATUS "CMAKE_TOOLCHAIN_FILE_FIX=${CMAKE_TOOLCHAIN_FILE_FIX}")

add_executable(cmake_toolchain_var_bug main.cpp)
