# Vscode Project Template for Yocto Project Cross-Compile Environment
## Introduction
This is a vscode project template for yocto project cross-compile environment. It is based on the [yocto project](https://www.yoctoproject.org/) and [vscode](https://code.visualstudio.com/). It is a simple and easy-to-use template for yocto project cross-compile environment. It can be used to develop and debug applications on the target board. It can also be used to develop and debug applications on the host machine.

## Needed vscode extensions
- C/C++ (ms-vscode.cpptools)
- C/C++ Extension Pack (ms-vscode.cpptools-extension-pack)
- CMake (twxs.cmake)
- CMake Tools (ms-vscode.cmake-tools)
- Task Explorer (spmeesseman.vscode-taskexplorer)

## Target board prerequisites for debugging
- gdbserver
- gdb
- openssh-server

## Setup your `cmake-kits.json` file
The cmake-kits.json file is used to configure the cross-compile environment. You need to modify the following parameters according to your own situation:
```json
[
    {
        "name": "Yocto-Poky: GCC/G++ for x86_64-pokysdk-linux",
        "compilers": {
            "C": "/opt/poky/3.3.4/sysroots/x86_64-pokysdk-linux/usr/bin/x86_64-poky-linux/x86_64-poky-linux-gcc",
            "CXX": "/opt/poky/3.3.4/sysroots/x86_64-pokysdk-linux/usr/bin/x86_64-poky-linux/x86_64-poky-linux-g++"
        },
        "environmentSetupScript": "/opt/poky/3.3.4/environment-setup-corei7-64-poky-linux",
        "toolchainFile": "/opt/poky/3.3.4/sysroots/x86_64-pokysdk-linux/usr/share/cmake/OEToolchainConfig.cmake"
    }
]
```
## Setup your `settings.json` file for debugging and deploying to the target
The settings.json file is used to configure the debugging and deployment environment. You need to modify the following parameters according to your own situation:

```json
{
    "customVariables": {
        // Target
        "TARGET_IP": "192.168.2.100",
        "TARGET_GDB_PORT": "3000",
        "TARGET_SSH_USER": "root",
        "TARGET_SSH_PASSWORD": "",
        "TARGET_EXECUTABLE_PATH": "/home/root",
        "TARGET_ARCHITECTURE": "x86_64",
        "EXECUTABLE_NAME": "helloWorld",
        // Host
        "HOST_EXECUTABLE_PATH": "${workspaceFolder}/bin",
    }
}
```

## Select the active kit
You can select the active kit by clicking the "Select a Kit" button in the lower left corner of the vscode window. The active kit is the cross-compile environment you want to use.
<p align="center"><img src="docs/resources/cmake_kit_selection.png" alt="CMake Kit Selection" width="600"/></p>

## Select build variant and build
You can select the build variant by clicking the "Select a Build Variant" button in the lower left corner of the vscode window. The build variant is the build type you want to use.
For debugging with gdb, you need to select the "Debug" build variant. For deployment to the target, you need to select the "Release" build variant.
<p align="center"><img src="docs/resources/cmake_build_variant.png" alt="CMake Kit Selection" width="600"/></p>

## Using Tasks to Build, Deploy, and Debug
Tasks can be run by clicking the "Run Task" button in the lower left corner of the vscode window. The following tasks are provided:
- `CMake: Build`
- `CMake: Configure`
- `Deploy Executable`
- `Stop GDB Server`
- `Kill GDB Server`
- `Start GDB Server`

### Building and Deploying to the Target
If `CMake: Build` task is executed successfully, you can deploy the executable to the target by clicking the "Run Task" button in the lower left corner of the vscode window. Select the `Deploy Executable` task and click the "Run Selected Task" button.

### Debugging on the Target
If `CMake: Build` task is executed successfully, you can debug the executable on the target by clicking the "Run Task" button in the lower left corner of the vscode window. Select the `Start GDB Server` task and click the "Run Selected Task" button. Then select the `Run and Debug` tab in the left sidebar of the vscode window and select `Launch GDB Debugger` in the drop-down list. Click the "Start Debugging" button to start debugging.