cmake_minimum_required(VERSION 3.16)
project(uWebSockets)
set(CMAKE_CXX_STANDARD 17)

file(GLOB USOCKETS_SRC 
    uSockets/src/*.* 
    uSockets/src/*/*.*
    uSockets/src/*/*/*.*)
add_library(uSockets STATIC ${USOCKETS_SRC})
target_include_directories(uSockets PUBLIC uSockets/src)
target_link_libraries(uSockets PUBLIC z ssl crypto)
target_compile_definitions(uSockets PUBLIC LIBUS_USE_OPENSSL)