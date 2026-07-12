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

# Base directory holding Pi-hole's configuration and state (pihole.toml,
# dnsmasq.conf, the databases, ...). Packagers can relocate the whole tree with
#   cmake -DPIHOLE_INSTALL_DIR=/opt/pihole/etc ...
# The default matches the historical hardcoded location. This is a build-time
# knob only and does not add a runtime override.
set(PIHOLE_INSTALL_DIR "/etc/pihole" CACHE STRING "Base directory for Pi-hole configuration and state")
add_compile_definitions(PIHOLE_INSTALL_DIR="${PIHOLE_INSTALL_DIR}")

add_subdirectory(src)
