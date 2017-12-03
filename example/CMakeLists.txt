cmake_minimum_required(VERSION 2.8)

project(libev_example)

FILE(GLOB echo_srv_src
        "echo-server.c"
        "array-heap.c"
        )

FILE(GLOB udp_echo_src
        "udp-echo-server.c"
        "array-heap.c"
        )

FILE(GLOB tcp_echo_src
        "tcp-echo-server.c"
        "array-heap.c"
        )

SET(includes
        "../libev"
        "./include"
        )
INCLUDE_DIRECTORIES(${includes})

add_executable(echo_server ${echo_srv_src})
TARGET_LINK_LIBRARIES(echo_server ev pthread)

add_executable(udp_echo_server ${udp_echo_src})
TARGET_LINK_LIBRARIES(udp_echo_server ev pthread)

add_executable(tcp_echo_server ${tcp_echo_src})
TARGET_LINK_LIBRARIES(tcp_echo_server ev pthread)
