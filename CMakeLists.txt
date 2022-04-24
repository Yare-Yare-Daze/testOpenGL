cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

set(Project_Name BattleCity)

project(${Project_Name})

add_executable(${Project_Name} src/main.cpp)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL OFF CACHE BOOL "" FORCE)

add_subdirectory(external/glfw)
target_link_libraries(${Project_Name} glfw)