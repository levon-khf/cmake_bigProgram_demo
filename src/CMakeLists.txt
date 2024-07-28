project(a)



add_executable(${PROJECT_NAME} main.cpp process)
target_link_libraries(${PROJECT_NAME} PUBLIC process)
target_include_directories(${PROJECT_NAME} PUBLIC ${PROCESS_DIR})

add_subdirectory(process)
add_subdirectory(map)