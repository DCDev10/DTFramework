# demo/CMakeLists.txt
add_executable(demo_app main.cpp)
target_link_libraries(demo_app PRIVATE project_core)