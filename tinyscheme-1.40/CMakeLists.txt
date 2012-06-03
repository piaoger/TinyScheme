cmake_minimum_required(VERSION 2.8)
project(TinyScheme)

file(GLOB ALL_SOURCE *.c)
file(GLOB ALL_CODE *.[ch])

set_source_files_properties(${ALL_SOURCE} COMPILE_FLAGS "-DSUN_DL=1 -DUSE_DL=1 -DUSE_MATH=0 -DUSE_ASCII_NAMES=0 -DUSE_INTERFACE=1 -DUSE_ERROR_HOOK=1 -DSHOW_ERROR_LINE=1")

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/init.scm ${SLI_BINARY_DIR}/)


#set the warning level
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wno-char-subscripts -O")

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS} -Wall -Wno-char-subscripts -g -O0")

add_library(tinyscheme SHARED ${ALL_SOURCE})
target_link_libraries(tinyscheme)