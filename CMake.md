# CMake

---

# 添加第三方库

```cmake
set(INC_DIR  ./lib/openssl/include)	# 头文件目录
set(LINK_DIR  ./lib/openssl/MD)	# 库目录

include_directories(${INC_DIR})
link_directories(${LINK_DIR})
link_libraries(libssl libcrypto)	# 要链接的库

add_executable(test test.cpp headers.h)

target_link_libraries(test libssl libcrypto)
```

