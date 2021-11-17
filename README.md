# rpmsg_cpp_compatibility
A test case for https://github.com/STMicroelectronics/STM32CubeMP1/pull/7

You mast have installed:
 * git
 * git lfs
 * cmake
 
 To build:
  * Download the repo

  `git clone git@github.com:sergeyblagodarnyy/rpmsg_cpp_compatibility.git`
  * Enter to the directory

  `cd rpmsg_cpp_compatibility`
  * Init and update submodules
 
`git submodule init`

`git submodule update`
  * Extract the arm-none-eabi goolchain 
  
  `7z x arm-tools/gcc-arm-none-eabi/gcc-arm-none-eabi-10-2020-q4-major.7z -aos -oarm-tools/gcc`
  * Run cmake using toolchain file

  `cmake -DCMAKE_TOOLCHAIN_FILE=arm-tools/toolchain.cmake -DCMAKE_BUILD_TYPE=Debug .`
  * Build
  
  `cmake --build . -v`
  
