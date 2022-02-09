cmake_minimum_required(VERSION 3.19.8)

project(2hol_cmake)

add_subdirectory(./lib/minorGems)

add_subdirectory(./bins/client)
# add_subdirectory(./bins/editor)
add_subdirectory(./bins/server)
