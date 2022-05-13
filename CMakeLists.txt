cmake_minimum_required(VERSION 3.21)
project(spatial_rotation_visualization)

set(CMAKE_CXX_STANDARD 14)

find_package(OpenGL REQUIRED)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# Including GLFW
add_subdirectory(glfw)
include_directories(glfw/include)

# Including GLAD
include_directories(glad/include)

# Including GLM
include_directories(glm)

include_directories(imgui-1.87)
include_directories(imgui-1.87/backends)

set(SOURCE_FILES src/main.cpp
        glad/src/glad.c
        imgui-1.87/imgui.cpp imgui-1.87/imgui_demo.cpp imgui-1.87/imgui_draw.cpp imgui-1.87/imgui_tables.cpp imgui-1.87/imgui_widgets.cpp
        imgui-1.87/backends/imgui_impl_glfw.cpp imgui-1.87/backends/imgui_impl_opengl3.cpp src/shader.h)

add_executable(${CMAKE_PROJECT_NAME} ${SOURCE_FILES})

# Linking GLFW and OGL
target_link_libraries(${CMAKE_PROJECT_NAME} glfw ${GLFW_LIBRARIES} ${OPENGL_LIBRARY})
