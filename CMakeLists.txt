cmake_minimum_required (VERSION 3.8)

project(hello-world-gen)

add_executable (${PROJECT_NAME} "src/main.cpp")

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory("external/glfw")

option(CGLM_SHARED "Shared build" ON)
option(CGLM_STATIC "Static build" OFF)
option(CGLM_USE_C99 "" OFF) # C11
option(CGLM_USE_TEST "Enable Tests" OFF)
add_subdirectory("external/cglm")

include_directories("external/KHR" "external/glad")

target_link_libraries(${PROJECT_NAME} glfw cglm)