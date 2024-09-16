cmake_minimum_required(VERSION 3.10)
project(MyProject)

option(BUILD_SHARED_LIBS "Build shared libraries" ON)

add_library(mylib ${LIBRARY_TYPE} mylib.cpp)

target_include_directories(mylib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

add_executable(program main.cpp)

target_link_libraries(program PRIVATE mylib)

if (NOT BUILD_SHARED_LIBS)
    target_link_libraries(program PRIVATE ${CMAKE_DL_LIBS})
endif()

install(TARGETS mylib program
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
    RUNTIME DESTINATION bin
)
