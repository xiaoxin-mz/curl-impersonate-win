# 我加的

根据下边教程编译出来的curl.exe libcurl.dll都是x64版本的，想要编译32位版本的，按照如下步骤：

## 安装msys2环境
1. Download and install MSYS2 (https://www.msys2.org/) into folder `c:\msys64\`
2. Run MSYS2 from start menu and update packages with command: `pacman -Suy`
3. Install additional packages: `pacman -S patch mingw-w64-i686-make mingw-w64-i686-cmake mingw-w64-i686-nasm mingw-w64-i686-gcc mingw-w64-i686-go`

## build
1. Clone this repository with --recursive attribute to get BoringSSL and Curl submodules.
2. Run script `copy_and_patch.bat` to copy original source codes to patchable directories and patch source code.
3. Run script `build_32.bat` to build binaries. Ready to use binaries are located within `curl\bin` folder.

## 生成lib
lib /def:libcurl.def /out:libcurl.lib /machine:x86

## 调用方式就跟正常版本一样了

# 到此为止

# curl-impersonate-win

A special build of curl for Windows that can impersonate Chrome and Safari.

Original idea and patches from https://github.com/lwthiker/curl-impersonate

# Version
Current version based on:
* Curl (https://github.com/curl/curl): v7.84.0
* BoringSSL (https://github.com/google/boringssl): 3a667d10e94186fd503966f5638e134fe9fb4080
* curl-impersonate (https://github.com/lwthiker/curl-impersonate): v0.5.4

# Environment
MSYS2 is needed to build binaries. Steps:
1. Download and install MSYS2 (https://www.msys2.org/) into folder `c:\msys64\`
2. Run MSYS2 from start menu and update packages with command: `pacman -Suy`
3. Install additional packages: `pacman -S patch mingw-w64-x86_64-make mingw-w64-x86_64-cmake mingw-w64-x86_64-nasm mingw-w64-x86_64-gcc mingw-w64-x86_64-go`

# Build
1. Clone this repository with --recursive attribute to get BoringSSL and Curl submodules.
2. Run script `copy_and_patch.bat` to copy original source codes to patchable directories and patch source code.
3. Run script `build.bat` to build binaries. Ready to use binaries are located within `curl\bin` folder.

In case if everything goes fine you should see this:

![image](https://user-images.githubusercontent.com/13541699/221516365-76990456-aeee-4c65-bd6c-2e9182f5c93a.png)

# Run
Executables and scripts are located inside release archive. Scripts can impersonate different browser, for example:

`curl_chrome104 --url https://www.google.com/search?q=cat --output google.html`

`curl_safari15_5 --url https://www.apple.com --output apple.html`
