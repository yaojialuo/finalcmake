# 查找 GTest 包
find_library(gtestd gtest HINTS "C:/Users/yaoji/source/repos/final/protobuf/build/_deps/googletest-src/build/lib/Debug/" required)
find_library(gtest_maind gtest_main HINTS "C:/Users/yaoji/source/repos/final/protobuf/build/_deps/googletest-src/build/lib/Debug/" required)
set(gtest ${gtestd} ${gtest_maind})
include_directories("C:/Users/yaoji/source/repos/final/protobuf/build/_deps/googletest-src/googletest/include")

# 创建测试目标
add_executable(TestMyLib test_main.cpp)
message("debugflag: ${CMAKE_CXX_FLAGS_DEBUG}")
string(REPLACE "/MDd" "/MTd" CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG}")
message("debugflag: ${CMAKE_CXX_FLAGS_DEBUG}")
# 链接库和 GTest 到测试目标
target_link_libraries(TestMyLib PRIVATE MyLib ${gtest})