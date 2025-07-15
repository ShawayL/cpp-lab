cmake_minimum_required(VERSION 3.20)
project(test_cpp_lab)

# 设置 CMAKE_PREFIX_PATH 指向你的安装目录
set(CMAKE_PREFIX_PATH "/home/luke/workspace/cpp/cpp-lab/out/install/unixlike-gcc-debug")

find_package(cpp_lab REQUIRED)

# 创建一个测试可执行文件
add_executable(test_app main.cpp)

# 链接到 cpp_lab::sample_library
target_link_libraries(test_app PRIVATE cpp_lab::sample_library)

# 获取并打印目标属性
get_target_property(INCLUDE_DIRS cpp_lab::sample_library INTERFACE_INCLUDE_DIRECTORIES)
get_target_property(COMPILE_DEFS cpp_lab::sample_library INTERFACE_COMPILE_DEFINITIONS)
get_target_property(COMPILE_FEATURES cpp_lab::sample_library INTERFACE_COMPILE_FEATURES)
get_target_property(LINK_LIBS cpp_lab::sample_library INTERFACE_LINK_LIBRARIES)
get_target_property(LIBRARY_TYPE cpp_lab::sample_library TYPE)
get_target_property(IMPORTED_LOCATION cpp_lab::sample_library IMPORTED_LOCATION)

message(STATUS "=== cpp_lab::sample_library Properties ===")
message(STATUS "Type: ${LIBRARY_TYPE}")
message(STATUS "Include Directories: ${INCLUDE_DIRS}")
message(STATUS "Compile Definitions: ${COMPILE_DEFS}")
message(STATUS "Compile Features: ${COMPILE_FEATURES}")
message(STATUS "Link Libraries: ${LINK_LIBS}")
message(STATUS "Imported Location: ${IMPORTED_LOCATION}")
message(STATUS "=========================================")

# 也打印一下依赖库的属性
get_target_property(OPTIONS_COMPILE_FEATURES cpp_lab::cpp_lab_options INTERFACE_COMPILE_FEATURES)
get_target_property(OPTIONS_COMPILE_OPTIONS cpp_lab::cpp_lab_options INTERFACE_COMPILE_OPTIONS)
get_target_property(OPTIONS_LINK_OPTIONS cpp_lab::cpp_lab_options INTERFACE_LINK_OPTIONS)

message(STATUS "=== cpp_lab::cpp_lab_options Properties ===")
message(STATUS "Compile Features: ${OPTIONS_COMPILE_FEATURES}")
message(STATUS "Compile Options: ${OPTIONS_COMPILE_OPTIONS}")
message(STATUS "Link Options: ${OPTIONS_LINK_OPTIONS}")

get_target_property(WARNINGS_COMPILE_OPTIONS cpp_lab::cpp_lab_warnings INTERFACE_COMPILE_OPTIONS)
message(STATUS "=== cpp_lab::cpp_lab_warnings Properties ===")
message(STATUS "Compile Options: ${WARNINGS_COMPILE_OPTIONS}")
message(STATUS "===========================================")
