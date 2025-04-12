cmake_minimum_required(VERSION 3.20)
project(DTFramework LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Thư mục con
add_subdirectory(src)
add_subdirectory(tests)
add_subdirectory(demo)

set_target_properties(project_core PROPERTIES FOLDER "Libraries")
set_target_properties(demo_app PROPERTIES FOLDER "Applications")

# Cấu hình compiler
if (CMAKE_CXX_COMPILER_ID MATCHES "Clang|GNU")
    add_compile_options(-Wall -Wextra -Wpedantic)
elseif (CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
    add_compile_options(/W4)
endif()

# Enable sanitizers cho debug builds
option(ENABLE_SANITIZERS "Enable sanitizers" ON)
if (ENABLE_SANITIZERS AND CMAKE_BUILD_TYPE MATCHES Debug)
    if (CMAKE_CXX_COMPILER_ID MATCHES "Clang|GNU")
        add_compile_options(-fsanitize=address,undefined,thread)
        add_link_options(-fsanitize=address,undefined,thread)
    endif()
endif()