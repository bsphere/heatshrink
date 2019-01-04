cmake_minimum_required(VERSION 3.2)
set(PROJECT_NAME heatshrink_static)
project(${PROJECT_NAME})

file(GLOB HEADER_FILES heatshrink_*.h)
file(GLOB SOURCE_FILES heatshrink_*.c)

add_definitions(-DHEATSHRINK_DYNAMIC_ALLOC=0)

add_library(${PROJECT_NAME} SHARED ${SOURCE_FILES} ${HEADER_FILES})
set_property(TARGET ${PROJECT_NAME} PROPERTY C_STANDARD 99)

add_executable(test_heatshrink_static test_heatshrink_static.c)
target_link_libraries(test_heatshrink_static ${PROJECT_NAME})

include(GNUInstallDirs)
install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
