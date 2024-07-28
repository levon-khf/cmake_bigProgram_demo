cmake_minimum_required(VERSION 3.19.0)
project(planning
    VERSION 0.0.01 
    DESCRIPTION "a demo of CMake big prograrm"
    HOMEPAGE_URL "https://github.com/levon-khf/cmake_bigProgram_demo"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)

#变量设置 这里设置的变量会传到子目录里
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(PROCESS_DIR ${CMAKE_SOURCE_DIR}/src/process)
set(MAP_DIR ${CMAKE_SOURCE_DIR}/src/map)
#添加子目录
add_subdirectory(src)


find_program(DOT_EXECUTABLE dot)
if(DOT_EXECUTABLE)
    add_custom_command(
        OUTPUT my_graph.png
        COMMAND ${DOT_EXECUTABLE} -Tpng my_graph.dot -o my_graph.png
        DEPENDS my_graph.dot
        COMMENT "Generating graph with Graphviz"
    )
    add_custom_target(generate_graph ALL DEPENDS my_graph.png)
endif()