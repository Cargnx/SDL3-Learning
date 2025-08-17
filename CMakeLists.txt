cmake_minimum_required(VERSION 4.0)
project(SDL3_Learning)

set(CMAKE_CXX_STANDARD 20)

# SDL3
find_package(SDL3 REQUIRED)
if (SDL3_FOUND)
    message(STATUS "SDL3 include dir: ${SDL3_INCLUDE_DIRS}")
endif ()

# ImGui
set(IMGUI_SRC
        Dependencies/imgui/imgui.cpp
        Dependencies/imgui/imgui_draw.cpp
        Dependencies/imgui/imgui_widgets.cpp
        Dependencies/imgui/imgui_tables.cpp
        Dependencies/imgui/imgui_demo.cpp
        Dependencies/imgui/backends/imgui_impl_sdl3.cpp
)

add_executable(SDL3_Learning main.cpp ${IMGUI_SRC})
target_include_directories(SDL3_Learning PRIVATE Dependencies/imgui
        Dependencies/imgui/backends
        ${SDL3_INCLUDE_DIRS})
target_link_libraries(SDL3_Learning PRIVATE SDL3::SDL3)
