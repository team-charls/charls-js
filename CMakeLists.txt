# SPDX-FileCopyrightText: © 2020 Chris Hafey, Team CharLS
# SPDX-License-Identifier: BSD-3-Clause

cmake_minimum_required(VERSION 3.22...4.3)

project (charlsjs VERSION 0.10.0 LANGUAGES CXX)

# The CMake project version is leading: use it to generate package.json
set(DIST_DIR "${CMAKE_SOURCE_DIR}/dist")
configure_file(
    ${CMAKE_SOURCE_DIR}/npm/package.json.in
    ${DIST_DIR}/package.json
    @ONLY
)

# Enable WebAssembly native exception handling. Required for CharLS error handling.
# Must be set before adding any subdirectory that uses this flag.
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fwasm-exceptions")

# set the build type if not specified
set(default_build_type "Release")
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message(STATUS "Setting build type to '${default_build_type}' as none was specified.")
  set(CMAKE_BUILD_TYPE "${default_build_type}")
endif()

if(NOT EXISTS "${PROJECT_SOURCE_DIR}/extern/charls/CMakeLists.txt")
    message(FATAL_ERROR "dependency charls is not present, please run: git submodule update --init --recursive")
endif()

if(NOT EMSCRIPTEN)
  message(FATAL_ERROR "Emscripten is required to build. Use emcmake cmake ..")
endif()

add_subdirectory(extern/charls EXCLUDE_FROM_ALL)
add_subdirectory(src)
