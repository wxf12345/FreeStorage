﻿# FreeStorage
## WINDOWS+ROCm A卡版本llama.cpp自己编译版本
1. 安装visualstudio 2022社区版并c++桌面开发套件
2. 安装strawberry-perl
3. 【可选】安装Git
4. 下载并安装ROCm
   下载地址：https://www.amd.com/en/developer/resources/rocm-hub/hip-sdk.html
5. 添加下面这些到环境变量

C:\Program Files\AMD\ROCm\5.7\bin

C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin

C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\Ninja

C:\Program Files\Git\bin

C:\Strawberry\perl\bin

7. 克隆llama.cpp到llama.cpp文件夹，进入文件夹并新建build文件夹，进入build

```
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
mkdir build
cd build
```
   
9.  编译llama.cpp
    
    gpu版本参考：https://rocm.docs.amd.com/projects/install-on-windows/en/latest/reference/system-requirements.html
   
   7900xt/7900xtx使用gfx1100
   ```
    cmake .. -G "Ninja" -DCMAKE_BUILD_TYPE=Release -DLLAMA_HIPBLAS=ON -DCMAKE_C_COMPILER="clang.exe" -DCMAKE_CXX_COMPILER="clang++.exe" -DAMDGPU_TARGETS="gfx1100"
   ```
   7700xt/7800xt使用gfx1101
   ```
    cmake .. -G "Ninja" -DCMAKE_BUILD_TYPE=Release -DLLAMA_HIPBLAS=ON -DCMAKE_C_COMPILER="clang.exe" -DCMAKE_CXX_COMPILER="clang++.exe" -DAMDGPU_TARGETS="gfx1101"
   ```
11. 构建
    ```
    cmake --build . -j
    ```
    llama.cpp/build/bin里面就会包含编译好的exe


  
