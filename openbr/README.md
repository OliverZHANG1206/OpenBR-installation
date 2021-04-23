### Modification log:
    1. Error of "Could not find a configuration file for package "OpenCV" that is compatible with requested version "2.4.5"."
        The method to solve this is to eliminate the version of OpenCV:
        **"find_package(OpenCV 2.4.5 REQUIRED)" --> find_package(OpenCV REQUIRED)
        
    2. The warning about "The OLD behavior for policy CMP0020 will be removed from a future version of CMake."
        This is only a warning that the future version will not support OLD behavior policy. This is not very important as it could still remains in CMakeLists.
        
    3. The warning about "qt5_use_modules is not part of the official API, and might be removed in Qt 6."
        There are nine warnings regards this. This is due to the usage of "qt5_add_resources".
        Therefore, regarding these warning loaction, I have changed four CMakeLists: ../openbr/CMakeLists.txt, ../app/br/CMakeLists.txt, ../app/examples/CMakeLists.txt, ../app/br-gui/CMakeLists.txt.
        **"qt5_add_resources(br ${QT_DEPENDENCIES})" --> "target_link_libraries(br ${QT_DEPENDENCIES})"**
        **"qt5_add_resources(br-gui ${QT_DEPENDENCIES})" --> "target_link_libraries(br-gui ${QT_DEPENDENCIES})"**
        **"qt5_use_modules(${EXAMPLE_BASENAME} ${QT_DEPENDENCIES}) --> "target_link_libraries(${EXAMPLE_BASENAME} ${QT_DEPENDENCIES})"**
        
    3. The warning about "Compatibility with CMake < 2.8.12 will be removed from a future version of CMake."
        I have modified the minimum version to 2.8.12 to suppress the warning of CMake in CMakeLists at ../openbr/janus/
        **"cmake_minimum_required(VERSION 2.8.6)" --> "cmake_minimum_required(VERSION 2.8.12)"**
