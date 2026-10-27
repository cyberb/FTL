# Pi-hole: A black hole for Internet advertisements
# (c) 2020 Pi-hole, LLC (https://pi-hole.net)
# Network-wide ad blocking via your own hardware.
#
# FTL Engine
# /CMakeList.txt
#
# This file is copyright under the latest version of the EUPL.
# Please see LICENSE file for your rights under this license.

# C17 supports requires minimum CMake version 3.21
# GCC 8.1.0
# LLVM Clang 7.0.0
cmake_minimum_required(VERSION 3.21)
set(CMAKE_C_STANDARD 17)

project(PIHOLE_FTL C)

set(DNSMASQ_VERSION pi-hole-v2.93)

set(PIHOLE_SCRIPT "/usr/local/bin/pihole" CACHE STRING "Path of the pihole script FTL runs for gravity updates")
if(NOT PIHOLE_SCRIPT MATCHES "^/")
    message(FATAL_ERROR "PIHOLE_SCRIPT must be an absolute path, got \"${PIHOLE_SCRIPT}\"")
endif()
add_compile_definitions(PIHOLE_SCRIPT="${PIHOLE_SCRIPT}")

option(FTL_EXIT_ON_RESTART "Exit with the restart code instead of re-executing FTL, leaving the restart to a supervisor" OFF)
if(FTL_EXIT_ON_RESTART)
    add_compile_definitions(FTL_EXIT_ON_RESTART)
endif()

add_subdirectory(src)
