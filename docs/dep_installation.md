# Dependencies Installation

This document provides guidance for installing the CARLA fork of Unreal Engine 4.26 and other software dependencies.
A large portion of it was created based on the official [__CARLA website__](https://carla.readthedocs.io/en/latest/build_windows/). Our tutorial adds the ability to run CARLA in the Virtual Reality environment using the Unreal Engine 4 (UE4) and the Oculus Quest headset. Please read carefully and follow all the steps, and the installation can take anywhere from 6 to 12 hours, depending on the hardware specification.

## Hardware Requirements
* __x64 system.__   Linux configuration is possible, but this instruction only covers Windows. 
* __200 GB disk space.__ Our customized CARLA package will take around 45 GB and the related major software installations (including UE4) will take 155 GB.
* __An adequate GPU.__ NVIDIA GTX 1080 TI and above is required. In order to run the simulation at optimal quality, NVIDIA RTX 3080 and above is recommended.
                      The GPU should have at least 8 GB of dedicated memory, although 16 GB is recommended.
* __Two TCP ports.__ 2000 and 2001 by default. Make sure that these ports are not blocked by firewalls or any other applications.

## Software Requirements
* [__Make__](http://gnuwin32.sourceforge.net/packages/make.htm) Install Make 3.8.1 by choosing “Complete package, except sources” from the download list. In the last step of installation, select “Download Sources”. Check your Make version by running ```make --version``` in a terminal. If you get the error: _'make' is not recognized as an internal or external command, operable program or batch file_, then Make is not successfully installed or added to path.
* [__CMake__](https://cmake.org/download/) Install CMake using the Windows x64 Installer. Check your CMake version by running: ```cmake --version``` in a terminal,
If you get the error _'cmake' is not recognized as an internal or external command, operable program or batch file_, then CMake is not successfully installed or added to path.
* [__Git__](https://git-scm.com/download/win) Install Git using the 64-bit Windows Installer. Accept all defaults.
* [__7Zip__](https://www.7-zip.org/) Install 7-zip using the x64 Windows Installer. Accept all defaults.

## Python
__1.__ Install [__Python 3.8.10__](https://www.python.org/downloads/release/python-3810/) 
using the 64-bit Windows Installer. When prompted, add Python to system path. Check your Python version using ```python --version```.

__2.__ Upgrade pip and install the required dependencies.
```sh
    pip3 install --upgrade pip
    pip3 install --user setuptools
    pip3 install --user wheel
```

## Visual Studio 2019
Download [__Visual Studio 2019__](https://developerinsider.co/download-visual-studio-2019-web-installer-iso-community-professional-enterprise/)
       and choose __Community__ version. Using the installer to add the following packages (will take about 20GB):

* __Windows 8.1 SDK (your windows version)__ Select it in the Installation details section on the right or go to the Indivdual Components tab and look under the SDKs, libraries, and frameworks heading.
* __x64 Visual C++ Toolset.__ In the Workloads section, choose Desktop development with C++. This will enable a x64 command prompt that will be used for the build. Check that it has been installed correctly by pressing the Windows button and searching for x64. Be careful not to open a x86_x64 prompt.
* __.NET framework 4.6.2.__ In the Workloads section, choose .NET desktop development and then in the Installation details panel on the right, select .NET Framework 
4.6.2 development tools. This is required to build Unreal Engine.

## CARLA Unreal Engine 4.26
__1.__ Download the modified version of the Unreal Enginer from [here](https://github.com/CarlaUnreal/UnrealEngine/releases/tag/0.9.13). <br />
__2.__ Navigate into the UE4 source folder, and run the configuration scripts:
```sh
    Setup.bat
    GenerateProjectFiles.bat
``` 
__3.__ Build the Engine:

* Open the `UE4.sln` file inside the source folder with Visual Studio 2019.

* In the build bar ensure that you have selected 'Development Editor', 'Win64' and 'UnrealBuildTool' options.
        
* In the solution explorer, right-click `UE4` and select `Build`.

* The build can take __a few hours__, depending on your hardware specification.

* Once the solution is compiled you can open the engine to check that everything was installed correctly by launching the executable `Engine\Binaries\Win64\UE4Editor.exe`.

If the installation was successful, this should be recognised by Unreal Engine's version selector. You can check this by right-clicking on any `.uproject` file and selecting `Switch Unreal Engine version`. You should see a pop-up showing `Source Build at PATH` where PATH is the installation path that you have chosen. If you can not see this selector or the `Generate Visual Studio project files` when you right-click on `.uproject` files, something went wrong with the Unreal Engine installation and you will likely need to reinstall it correctly.

## CARLA 0.9.13 Project
__1.__ Download the project source code from [__here__](https://drive.google.com/drive/folders/1ay0wchAReZGwusN_fJR9NehLhK8c_jHJ).
Unzip the project into a standalone directory. <br />
__2.__ Navigate into the CARLA project directory and run command `make launch` in the __x64 Native Tools Command Prompt for Visual Studio 2019__. <br />
__3.__ After a few minutes, you will see "launching unreal editor" and the UE4 window will pop up. During the loading process, the UE4 window will stop at 95% progress for approximately __1-2 hours__. Be patient and let the process finish. After successfully entering the UE4, you will see "Building Mesh Distance Fields" and "Compiling Shaders", which can also take __1-2 hours__ to finish.

## OpenXR
__1.__ Install Windows [__Oculus Application__](https://store.facebook.com/quest/setup/) and accept all defaults. <br />
__2.__ Login with your Oculus account or sign up for one. <br />
__3.__ Configure and Install the OpenXR Runtime for Oculus follwing the instructions in [__here__](https://docs.unrealengine.com/4.26/en-US/SharingAndReleasing/XRDevelopment/OpenXR/openxr_prerequisites/). Follow the instructions in the Oculus section. <br />
__4.__ Turn on the Oculus application, go to __Settings__ > __General__. Under __OpenXR Runtime__, make sure "Oculus is set as the active OpenXR Runtime".

## G29 Wheel
__1.__ Download the wheel support package from [here](www.google.com) and extract it into a folder called G29. <br />
__2.__ Download and install Logitech G Hub from [here](https://www.logitechg.com/en-us/innovation/g-hub.html). <br />
__3.__ Plug the wheel into the computer, and make sure the wheel self calibrates to the center. <br />
__4.__ If something goes wrong, check for wheel conenction in the Logitech G Hub.