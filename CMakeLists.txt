cmake_minimum_required(VERSION 3.30.2)
project(planning)
set(CMAKE_CXX_STANDARD 17)

#保证动态库和exe都在bin目录下
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin) 
#Linux操作系统 : CMAKE_LIBRARY_OUTPUT_DIRECTORY
#Linux只静态库 ：CMAKE_ARCHIVE_OUTPUT_DIRECTORY

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
add_library(common
SHARED
${SRC_LISTS}
)

target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)


add_executable(planning_main planning_main.cpp)

target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

target_link_libraries(planning_main
PUBLIC
common
)