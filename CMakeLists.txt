cmake_minimum_required(VERSION 2.8)
project(usbtop)

set (VERSION_MAJOR 0)
set (VERSION_MINOR 3)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR}/cmake)

find_package(PCAP REQUIRED)
include_directories(${PCAP_INCLUDE_DIR})

find_package(Boost)
if (NOT ${Boost_FOUND})
  # If boost can't be found, use our own version
  include_directories(third-party)
else()
  include_directories(${Boost_INCLUDE_DIR})
endif()

include_directories(include)
add_subdirectory(src)
