cmake_minimum_required(VERSION 3.0)

project(PDCurses)

if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()

if(CMAKE_C_COMPILER_ID STREQUAL "GNU" AND CMAKE_BUILD_TYPE STREQUAL "Release")
    add_compile_options(-s)
endif()

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

file(GLOB SRC_PDCURSES ${CMAKE_CURRENT_SOURCE_DIR}/pdcurses/*.c)
file(GLOB SRC_HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/*.h)
file(GLOB SRC_WINCON ${CMAKE_CURRENT_SOURCE_DIR}/wincon/*.c)
file(GLOB SRC_WINCON_H ${CMAKE_CURRENT_SOURCE_DIR}/wincon/*.h)

add_library(pdcurses STATIC
    ${SRC_PDCURSES}
    ${SRC_HEADERS}
    ${SRC_WINCON}
    ${SRC_WINCON_H})

add_definitions(-DPDC_WIDE -DPDC_FORCE_UTF8)
