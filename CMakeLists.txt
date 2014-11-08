#cmake version
cmake_minimum_required(VERSION 2.8)
project(MazeSolver)

if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
		message(STATUS "Setting build type to 'Release as none was specified.")
		set(CMAKE_BUILD_TYPE Release CACHE STRING "Choose the type of build." FORCE)
		#set possible values of built type for cmake-gui
		set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Release" "Debug"
						"MinSizeRel" "RelWithDebInfo")
endif()

set(EXECUTABLE_NAME "MazeSovler")
set(VERSION_MAJOR 0)
set(VERSION_MINOR 1)
configure_file(
				"${PROJECT_SOURCE_DIR}/config.h.in"
				"${PROJECT_BINARY_DIR}/config.h"
				)

set(HEADERS
				src/mazeGen/disjointSets.hpp
				src/mazeGen/mazeGen.hpp
				src/mazeGen/cls.hpp
)

set(SOURCES
				src/mazeGen/disjointSets.cpp
				src/mazeGen/mazeGen.cpp
				src/main.cpp
)

include_directories("${PROJECT_BINARY_DIR}")
include_directories("${PROJECT_SOURCE_DIR}/src/mazeGen")
include_directories("${PROJECT_SOURCE_DIR}/src/mazeSolve")

add_executable(${EXECUTABLE_NAME} ${SOURCES} ${HEADERS})
