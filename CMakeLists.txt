cmake_minimum_required(VERSION 2.6)
project(hqx)

set(IL_TESTS OFF CACHE BOOL "" FORCE)
add_subdirectory(lib/DevIL/DevIL)

add_executable(${PROJECT_NAME} src/hq2x.c src/hq3x.c src/hq4x.c src/hqx.c src/init.c)

target_include_directories(${PROJECT_NAME}
    PUBLIC include
    PUBLIC lib/DevIL/DevIL/include
)

target_link_libraries(${PROJECT_NAME}
    IL
)

file (GLOB_RECURSE RESOURCES resources/*.*)
foreach(RESOURCE ${RESOURCES})
configure_file(${RESOURCE} ${CMAKE_CURRENT_BINARY_DIR} COPYONLY)
endforeach(RESOURCE ${RESOURCES})
