# Dependencies Installation

This document provides guidance for installing the CARLA fork of Unreal Engine 4.26 and other software dependencies.

## Hardware Requirements
* __x64 system__ 
* __180 GB disk space__ 
* __An adequate GPU__
* __Two TCP ports and good internet connection__ 
* __Oculus Quest 2__
* __Logitech G29 Wheel__

## Software Requirements
* __Visual Studio 2019__   
    * __Windows 8.1 SDK.__ 
    * __x64 Visual C++ Toolset__ 
    * __.NET framework 4.6.2__
* __Git__
* __7Zip__ 
* __Python3 x64__
* __Oculus Desktop App__
* __OpenXR for Oculus__

## Install CARLA fork of Unreal Engine 4.26
To build the modified version of Unreal Engine:

__1.__ Download the source code from [this release](https://github.com/CarlaUnreal/UnrealEngine/releases/tag/0.9.13).

__2.__ Run the configuration scripts:

```sh
    Setup.bat
    GenerateProjectFiles.bat
```

__3.__ Compile the modified engine:

>1. Open the `UE4.sln` file inside the source folder with Visual Studio 2019.

>2. In the build bar ensure that you have selected 'Development Editor', 'Win64' and 'UnrealBuildTool' options. Check [this guide](https://docs.unrealengine.com/en-US/ProductionPipelines/DevelopmentSetup/BuildingUnrealEngine/index.html) if you need any help. 
        
>3. In the solution explorer, right-click `UE4` and select `Build`.

__4.__ Once the solution is compiled you can open the engine to check that everything was installed correctly by launching the executable `Engine\Binaries\Win64\UE4Editor.exe`.

If the installation was successful, this should be recognised by Unreal Engine's version selector. You can check this by right-clicking on any `.uproject` file and selecting `Switch Unreal Engine version`. You should see a pop-up showing `Source Build at PATH` where PATH is the installation path that you have chosen. If you can not see this selector or the `Generate Visual Studio project files` when you right-click on `.uproject` files, something went wrong with the Unreal Engine installation and you will likely need to reinstall it correctly.

## Set up Oculus Quest 2
__1.__ Follow [this document](https://support.oculus.com/articles/headsets-and-accessories/oculus-link/connect-link-with-quest-2/) to enable Oculus Link.

__2.__ Follow [this blog](https://developer.oculus.com/blog/openxr-for-oculus/) to set up OpenXR for Oculus.
