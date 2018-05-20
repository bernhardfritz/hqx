cmake_minimum_required(VERSION 2.6)
project(hqx)

set(IL_TESTS OFF CACHE BOOL "" FORCE)
add_subdirectory(lib/DevIL/DevIL)

include_directories(
    include
    lib/DevIL/DevIL/include
)

add_library(hqx_library STATIC
    src/hq2x.c
    src/hq3x.c
    src/hq4x.c
    src/init.c
)
set_target_properties(hqx_library
    PROPERTIES OUTPUT_NAME hqx
)

add_executable(hqx_executable
    src/hqx.c
)
target_link_libraries(hqx_executable
    IL
    hqx_library
)
set_target_properties(hqx_executable
    PROPERTIES OUTPUT_NAME hqx
)

install(TARGETS hqx_library DESTINATION lib)
install(TARGETS hqx_executable DESTINATION bin)
