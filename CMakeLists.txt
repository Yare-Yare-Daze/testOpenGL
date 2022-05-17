cmake_minimum_required(VERSION 3.20 FATAL_ERROR)

set(Project_Name BattleCity)
project(${Project_Name})

add_executable(${Project_Name} 
	src/main.cpp
	src/Renderer/ShaderProgram.cpp
	src/Renderer/ShaderProgram.h
	src/Renderer/Texture2D.cpp
	src/Renderer/Texture2D.h
	src/Resources/ResourceManager.cpp
	src/Resources/ResourceManager.h
	src/Resources/stb_image.h
	)

target_compile_features(${Project_Name} PUBLIC cxx_std_17)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL OFF CACHE BOOL "" FORCE)

add_subdirectory(external/glfw)
target_link_libraries(${Project_Name} glfw)

add_subdirectory(external/glad)
target_link_libraries(${Project_Name} glad)

set_target_properties(${Project_Name} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/)

add_custom_command(TARGET ${Project_Name} POST_BUILD
					COMMAND ${CMAKE_COMMAND} -E copy_directory
					${CMAKE_SOURCE_DIR}/res $<TARGET_FILE_DIR:${PROJECT_NAME}>/res/)