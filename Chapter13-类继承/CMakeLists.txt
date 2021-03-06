cmake_minimum_required(VERSION 3.0.0)
project(chapter13 VERSION 0.1.0)

include(CTest)
enable_testing()

#dubug 模式
set (CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -g")

# 添加头文件路径
include_directories("${PROJECT_SOURCE_DIR}/7_1")
include_directories("${PROJECT_SOURCE_DIR}/7_2")
include_directories("${PROJECT_SOURCE_DIR}/project0")
include_directories("${PROJECT_SOURCE_DIR}/project1")
include_directories("${PROJECT_SOURCE_DIR}/project2")
include_directories("${PROJECT_SOURCE_DIR}/exercise1")
include_directories("${PROJECT_SOURCE_DIR}/exercise2")
include_directories("${PROJECT_SOURCE_DIR}/exercise3")
include_directories("${PROJECT_SOURCE_DIR}/exercise4")

add_executable(test_project0 ./usett0.cpp)
add_executable(test_project1 ./usett1.cpp)
add_executable(project2_test ./usebrass2.cpp)
add_executable(exercise1_test ./exercise1_test.cpp)
add_executable(exercise2_test ./exercise2_test.cpp)
add_executable(exercise3_test ./exercise3_test.cpp)
add_executable(exercise4_test ./exercise4_test.cpp)
add_executable(7_1 ./7_1/7_1.cpp)
add_executable(7_2 ./7_2/7_2.cpp)
add_executable(Example05_test ./Example05_test.cpp)
add_executable(ABC_test ./ABC_test.cpp)

# 添加子目录
add_subdirectory(project0)
add_subdirectory(project1)
add_subdirectory(project2)
add_subdirectory(exercise1)
add_subdirectory(exercise2)
add_subdirectory(exercise3)
add_subdirectory(exercise4)

# 添加project0库
target_link_libraries(test_project0 project0)
target_link_libraries(test_project1 project1)
target_link_libraries(project2_test project2)
target_link_libraries(exercise1_test exercise1)
target_link_libraries(exercise2_test exercise2)
target_link_libraries(exercise3_test exercise3)
target_link_libraries(exercise4_test exercise4)
