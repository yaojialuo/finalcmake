# CMakeList.txt: finalcmake 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#cmake -B build -DCMAKE_VERBOSE_MAKEFILE=ON
#cmake --build build --config Debug
cmake_minimum_required (VERSION 3.8)
set(CMAKE_VERBOSE_MAKEFILE ON)
# 如果支持，请为 MSVC 编译器启用热重载。
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("finalcmake")

# 将源代码添加到此项目的可执行文件。
add_executable (finalcmake "finalcmake.cpp" "finalcmake.h" "hello.cpp")
add_library(libhello SHARED hello.cpp)
if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET finalcmake PROPERTY CXX_STANDARD 20)
endif()

# TODO: 如有需要，请添加测试并安装目标。
add_subdirectory(src)
