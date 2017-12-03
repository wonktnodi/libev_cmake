cmake_minimum_required(VERSION 2.8)
project(libev C)

set(CMAKE_C_STANDARD 99)

MESSAGE( STATUS "CMAKE_C_COMPILER: " ${CMAKE_C_COMPILER} )
MESSAGE( STATUS "CMAKE_binary_dir: " ${CMAKE_CURRENT_BINARY_DIR} )

include (../cmake/dist.cmake)
include (../cmake/configure.cmake)

configure_file ( ${CMAKE_SOURCE_DIR}/libev/config.h.cmake ${CMAKE_CURRENT_BINARY_DIR}/config.h )

include_directories( ${CMAKE_CURRENT_BINARY_DIR} )

set ( EV_SRC
        ev.c
        event.c
        #libev/ev_kqueue.c
        ev_wrap.h)


if (WIN32)
    list ( APPEND EV_LIBS Ws2_32 )
endif ()

add_library(ev STATIC ${EV_SRC})