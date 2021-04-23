## OpenBR-installation for OpenCV4.X above
### This package could install the OpenBR on VS2019 platform with OpenCV version is 4.X above. I have modified the CMakeLists.txt in the original Openbr folder.
### I used OpenCV 4.5.2, Qt 5.12.2, CMake 3.20.1 and VS2019 for the environment of building Openbr. The OpenBR official website: www.openbiometrics.org
#### #This is only used for learning, not for any commercial purposes.
The steps will be shown below:
 1. **Download Visual Studio 2019, Qt (5.12.2), CMake (minimum required: 2.8.12), OpenCV4.X and openbr in this folder.**  
   **Note: The Qt should download with "msvc2019_64" coponents at corresponding version**  
    * Link for downloading: **[Download](https://visualstudio.microsoft.com/zh-hans/vs/)** for VS2019; **[Download](https://www.qt.io/download)** for Qt; **[Download](https://cmake.org/download/)** for CMake; **[Download](https://opencv.org/releases/)** for OpenCV  
    * Once install all the softwares, please add "(opencv folder)..\opencv\build\x64\vc15\bin", "(CMake folder)..\Cmake\bin" and "(Qt folder)..\Qt\5.15.2\msvc2019_64\bin" to environment path on the conputer.  
 2. **Build OpenCV**  
    * Open CMake (CMake is in: ../bin/cmake-gui.exe.)  
    * Add "source code" (../opencv/sources)  
    * Create a new folder (Recommend: in the same folder in opencv) and put its path in CMake "binaries"  
    * Click "Configure", The generator choose "Visual Studio 16 2019" and choose "Use default native compiler". Then click "Finish".  
    * Once there is "Configuring done" shown below, find "BUILD_PERF_TESTS", "BUILD_TESTS" and "WITH_FFMPEG" oppitions and tick it off. Then click "Generate" and waiting for "Generating done".  
    * Click "Open Project", the VS2019 will be opened. Make sure the compiler is in "Debug" mode.  
    * Then choose "ALL_BUILD" in "CMakeTargets" folder at "Solution Explorer" and right-click "build".  
    * Once finished. Choose "INSTALL" and right-click "Project Only" -> "Build Only INSTALL".  
    * Change the compiler into "Release", then redo the above 2 steps.
 3. **Build OpenBR**  
    * Add "source code" (openbr path) and create a new folder and put the path in "binaries".  
    * Click "Configure", The generator choose "Visual Studio 16 2019" and choose "Use default native compiler". Then click "Finish".  
    * Once there is "Configuring done" shown below, search "CMAKE_INSTALL_PREFIX" and create a suitable install path for it. (Note: Do not use "/Program Files (x86)/openbr" folder as this might need administration to create) **Please ignore all the warnings, the warnings will not affect any installation.**
    * Then search "BR_INSTALL_DEPENDENCIES" and tick this options.  
    **If there are errors occours such that "OPENCV_DIR", "QT5_DIR" is not found, please check whether the corresponding environment path is added correctly. If the dir was added correctly but still could not find OpenCV, then add a OpenCV_DIR directly in CMake-gui. The correct dir should be like this: opencv/sources/build-msvc2019/install/x64/vc16/lib** 
    * Then Click "Add Entry", set name "CMAKE_PREFIX_PATH", choose type "String", add value "C:/OpenCV/4.5.2/opencv/sources/build-msvc2019/install;C:/Qt/5.15.2/msvc2019_64"
    **This value is the path of your built "install" folder of OpenCV and the path of your Qt "msvc2019_64" folder**  
    * Click "Generate" and waiting for "Generating done". Click "Open Project", the VS2019 will be opened.   
    * Select "Release" mode
    * Choose "All_BUILD" project at "Solution Explorer" and right-click. Choose "Build".  
    * Once finished. Choose "INSTALL" and right-click "Project Only" -> "Build".  
    **The building processure requires a download files. if the speed is relatively slow, you can download [here](http://github.com/biometrics/openbr/releases/download/v1.1.0/models.tar.gz). Download it and put it in "(openbr path)../models-prefix/src" folder.**
 4. **Hack OpenBR**
    * Open Qt (../Qt/Tools/QtCreator/bin/qtcreator.exe)  
    * From the Qt Creator "Tools" menu select "Options...". Under "Kits" select "Desktop Qt 5.15.2 MSVC2019 64bit(default)"  
    * "File" menu select "Open File or Project...". Select "openbr/CMakeLists.txt" then "Open".  
    * Select "Run CMake" then "Finish"  
 5. **Testing**
    * Puting the following code to the CMD  
      $ cd C:\openbr\build-msvc2013\install\bin (your building folder path)  
      $ br -gui -algorithm "Show(false)" -enroll 0.webcam  
    * if the camera is opened successfully, the openbr is successfully installed in computers  

Orginal installation guidance for OpenBR is on its website [here](http://openbiometrics.org/docs/install/).
