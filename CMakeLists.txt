cmake_minimum_required(VERSION 3.20)

project(OpenGLPractice)

set(CMAKE_CXX_STANDARD 20)

find_package(OpenGL REQUIRED)

find_package(PkgConfig REQUIRED)
pkg_search_module(GLEW REQUIRED glew)

find_path(GLEW_INCLUDE_DIR GL/glew.h PATHS /opt/homebrew/include)
find_library(GLEW_LIBRARY GLEW PATHS /opt/homebrew/lib)

include_directories(${GLEW_INCLUDE_DIR})
link_libraries(${GLEW_LIBRARY})

find_package(SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS})

add_executable(OpenGLPractice main.cpp)

target_link_libraries(OpenGLPractice PRIVATE ${GLEW_LIBRARY} ${SDL2_LIBRARIES} OpenGL::GL)