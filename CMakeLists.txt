cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

set(Project_Name BattleCity)
project(${Project_Name})

set(CMAKE_CXX_STANDART 17)
add_executable(${Project_Name} 
	src/main.cpp
	src/Renderer/ShaderProgram.cpp
	src/Renderer/ShaderProgram.h
	)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL OFF CACHE BOOL "" FORCE)

add_subdirectory(external/glfw)
target_link_libraries(${Project_Name} glfw)

add_subdirectory(external/glad)
target_link_libraries(${Project_Name} glad)