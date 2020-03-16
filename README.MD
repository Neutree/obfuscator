# LLVM Obfuscator 8.0.0

Visit the [Releases](https://github.com/badmannersteam/obfuscator/releases) page for win64 precompiled binaries.

## How to use with Android NDK

Add the following lines to the CMakeLists.txt of your application module and fix the path in the first line:

```cmake
set(LLVM_OBFUSCATOR_PATH "${CMAKE_CURRENT_LIST_DIR}/../tools/llvm_obfuscator_8")
set(CMAKE_C_COMPILER "${LLVM_OBFUSCATOR_PATH}/bin/clang.exe")
set(CMAKE_CXX_COMPILER "${LLVM_OBFUSCATOR_PATH}/bin/clang++.exe")

# Bogus control flow is really unstable
# set(OBFUSCATOR_FLAGS "-mllvm -sub -mllvm -fla -mllvm -sobf -mllvm -bcf")
set(OBFUSCATOR_FLAGS "-mllvm -sub -mllvm -fla -mllvm -sobf")

string(APPEND CMAKE_C_FLAGS " ${OBFUSCATOR_FLAGS}")
string(APPEND CMAKE_CXX_FLAGS " ${OBFUSCATOR_FLAGS}")
```
