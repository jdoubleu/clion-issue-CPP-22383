# Reproduce CLion issue
Link: https://youtrack.jetbrains.com/issue/CPP-22383

## Steps to reproduce
1. Open the project in CLion
2. Edit the Project Settings > Build, Execution, Deployment > CMake and
    1. add -DCMAKE_TOOLCHAIN_FILE=toolchains/test.cmake to the CMake options
3. Now delete the created cmake-build-debug folder. This might have been poisened already, when you opened the project in Clion.
4. After deleting, CLion will automatically reload the CMake config and recreate the folder. Please note:
    1. the CMake log output shows something around "Toolchain file path is absolute"
5. (Manually) re-load the CMake project. Please note:
    1. The CMake log output now displays an error message, because the CMAKE_TOOLCHAIN_FILE path is no longer absolute. The cmake command arguments (from CLion) have overwritten the cached variable.
