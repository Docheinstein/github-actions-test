cmake_minimum_required(VERSION 3.17)
project(github_actions_test)

set(CMAKE_CXX_STANDARD 17)

add_subdirectory(external)


add_executable(github_actions_test main.cpp)
target_link_libraries(github_actions_test PRIVATE zlibstatic)

