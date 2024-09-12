cmake_minimum_required(VERSION 3.10.2)
project(stb)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(stb INTERFACE)
target_include_directories(stb INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
    $<INSTALL_INTERFACE:include/stb>)

## installation configuration
install(TARGETS stb
    EXPORT xmotionTargets
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    INCLUDES DESTINATION include)

file(GLOB HEADER_FILES "${CMAKE_CURRENT_LIST_DIR}/stb_*.h")
install(FILES ${HEADER_FILES}
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/stb)
