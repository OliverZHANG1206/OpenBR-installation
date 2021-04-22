## OpenBR-installation for OpenCV4.X above
### This package could install the OpenBR on VS2019 platform with OpenCV version is 4.X above. I have modified the CMakeLists.txt in the orginal Openbr folder.
### I uses OpenCV 4.5.2, Qt 5.12.2, CMake 3.20.1 and VS2019 for the environment of building openbr. The OpenBR website: www.openbiometrics.org  
The steps will be shown below:
#### &emsp;1. Download Visual Studio 2019, Qt (5.12.2), CMake (minimum required: 2.8.12), OpenCV4.X and openbr in this folder.  
&emsp;&emsp;**Note: The Qt should download with "msvc2019_64" coponents at corresponding version**  
&emsp;&emsp;* Link for downloading: **[Download](https://visualstudio.microsoft.com/zh-hans/vs/)** for VS2019; **[Download](https://www.qt.io/download)** for Qt; **[Download](https://cmake.org/download/)** for CMake; **[Download](https://opencv.org/releases/)** for OpenCV  
&emsp;&emsp;* Once install all the softwares, please add "..\opencv\build\x64\vc15\bin", "..\Cmake\bin" and "\Qt\5.15.2\msvc2019_64\bin" to  
&emsp;&emsp;environment path on the conputer.
#### &emsp;2. Build OpenCV  
&emsp;&emsp;* Create a new folder and 
#### &emsp;3. Build OpenBR  
&emsp;&emsp;* CMake is in: camke folder../bin/cmake-gui.exe.  
&emsp;&emsp;* Add "source code": openbr path and create a new folder and put the path in "binaries".  
&emsp;&emsp;* Click "Configure", The generator choose "Visual Studio 16 2019" and choose "Use default native complier". Then click "Finish".  
&emsp;&emsp;* Once there is "Configuring done" shown below, search "CMAKE_INSTALL_PREFIX" and create a suitable install path for it. (Note: Do not  
&emsp;&emsp;using "/Program Files (x86)/openbr" folder as this might need administration to create)  
&emsp;&emsp;**If there are problems such that "OPENCV_DIR", "QT5_DIR" is not found, please check whether the corresponding environment path is  
&emsp;&emsp;added correctly.**  
&emsp;&emsp;* Click "Generate" and waiting for "Generating done". Click "Open Project", the VS2019 will be opened.
#### &emsp;4. Installing Openbr  
&emsp;&emsp;Choose "INSTALL" project at "Solution Explorer" and right-click. Choose "Build".
&emsp;&emsp;Waiting for finish.
#### &emsp;5. Hack OpenBR

