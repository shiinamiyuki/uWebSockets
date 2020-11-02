cmake_minimum_required(VERSION 3.16)
project(uWebSockets)
set(CMAKE_CXX_STANDARD 17)
option(UW_USE_SSL "Use OpenSSL for uWebSockets" OFF)
file(GLOB USOCKETS_SRC 
    uSockets/src/*.* 
    uSockets/src/*/*.*
    uSockets/src/*/*/*.*)
add_subdirectory(ext/libuv)
add_library(uSockets STATIC ${USOCKETS_SRC})
target_include_directories(uSockets PUBLIC uSockets/src)
if(UW_USE_SSL)
    target_link_libraries(uSockets PUBLIC  ssl crypto)
    target_compile_definitions(uSockets PUBLIC LIBUS_USE_OPENSSL)
endif()
target_link_libraries(uSockets PUBLIC uv)