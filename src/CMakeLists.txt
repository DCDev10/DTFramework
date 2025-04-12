# src/CMakeLists.txt

# Thu thập file .cpp và .h từ src và các thư mục con
file(GLOB SOURCES
    "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/core/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/event_system/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/threading/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/platform/*.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/logger/*.cpp"
)
file(GLOB HEADERS
    "${CMAKE_CURRENT_SOURCE_DIR}/*.h"
    "${CMAKE_CURRENT_SOURCE_DIR}/core/*.h"
    "${CMAKE_CURRENT_SOURCE_DIR}/event_system/*.h"
    "${CMAKE_CURRENT_SOURCE_DIR}/threading/*.h"
    "${CMAKE_CURRENT_SOURCE_DIR}/platform/*.h"
    "${CMAKE_CURRENT_SOURCE_DIR}/logger/*.h"
)

# Kiểm tra xem có file nguồn hay không
if(NOT SOURCES)
    message(WARNING "No source files (.cpp) found in src or its subdirectories. Please add .cpp files to src/core, src/event_system, etc.")
endif()
if(NOT HEADERS)
    message(WARNING "No header files (.h) found in src or its subdirectories. Please add .h files to src/core, src/event_system, etc.")
endif()

# Tạo thư viện tĩnh
add_library(project_core STATIC ${SOURCES} ${HEADERS})

# Include các thư mục header
target_include_directories(project_core PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/core
    ${CMAKE_CURRENT_SOURCE_DIR}/event_system
    ${CMAKE_CURRENT_SOURCE_DIR}/threading
    ${CMAKE_CURRENT_SOURCE_DIR}/platform
    ${CMAKE_CURRENT_SOURCE_DIR}/logger
)

# Hỗ trợ Visual Studio hiển thị cấu trúc thư mục
source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SOURCES} ${HEADERS})