cmake_minimum_required(VERSION 3.5)
project(client-server-app VERSION 0.0.1 DESCRIPTION "Client-Server for multi-platform" LANGUAGES CXX)

add_executable(server-binary server.cpp)
add_executable(client-binary client.cpp)

target_compile_features(server-binary PRIVATE cxx_std_11)
target_compile_features(client-binary PRIVATE cxx_std_11)

if(WIN32)
    target_link_libraries(server-binary PRIVATE ws2_32)
    target_link_libraries(client-binary PRIVATE ws2_32)
endif()
