cmake_minimum_required(VERSION 3.20)
project(rss_reader_tui CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_compile_options(-Wall -Wextra -Werror)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    add_compile_options(-fsanitize=address,undefined -g)
    add_link_options(-fsanitize=address,undefined)
endif()

add_library(core
    src/core/src/placeholder.cpp
)
target_include_directories(core PUBLIC src/core/include)

add_executable(rss_reader
    src/app/main.cpp
)
target_link_libraries(rss_reader PRIVATE core)
