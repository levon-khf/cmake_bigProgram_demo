project(test_map)

add_executable(${PROJECT_NAME} test.cpp)

target_include_directories(${PROJECT_NAME} PUBLIC ${MAP_DIR})
target_link_libraries(${PROJECT_NAME} PUBLIC map)

add_test(
    NAME test_map_info
    COMMAND ${PROJECT_NAME}
)