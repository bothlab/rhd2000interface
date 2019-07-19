project(RHD2000Interface)
cmake_minimum_required(VERSION 3.12)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)

set(PROJECT_VERSION 1.5.2)

#
# Options
#
option(MAINTAINER "Enable maintainer mode" OFF)
option(MORE_WARNINGS "Enable more compiler warnings" ON)


#
# Compiler flags
#
if (MORE_WARNINGS OR MAINTAINER)
    add_definitions("-Wall")

    if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
        add_definitions("-Wextra")
    endif()
endif()
if (MAINTAINER)
    if (NOT "${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
        add_definitions("-Werror")
    endif()
endif()

# Windows compat stuff
if ("${CMAKE_SYSTEM_NAME}" STREQUAL "Windows")
    if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
        add_definitions("-Wno-old-style-cast"
                        "-Wno-c++98-compat"
        )
    endif()
endif()


#
# Dependencies
#
include(GNUInstallDirs)
find_package(Threads)
find_package(Qt5 COMPONENTS Core Widgets Multimedia REQUIRED)

#
# Config
#
configure_file(config.h.in ${CMAKE_BINARY_DIR}/config.h)
include_directories(${CMAKE_BINARY_DIR})


#
# Subdirectories
#
add_subdirectory(source)
add_subdirectory(data)
