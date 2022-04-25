# Run Simulation

This document provides guidance for downloading, setting up, and running the simulation.

## Download the Project
The project can be downloaded from [this Google Drive folder](https://drive.google.com/drive/folders/1ay0wchAReZGwusN_fJR9NehLhK8c_jHJ?usp=sharing). Due to the enormous size of the project, it cannot be hosted on Github. You can use 7Zip to unzip the project.

## Run the VR simulation
### Set up the Oculus Headset (before setting up Unreal Engine)
__1.__ Turn on Oculus desktop program. 

__2.__ Turn on the headset.

__3.__ Allow device to access data from the computer using the controller.

__4.__ If Guardian is not found, create guardian using the controller.

__5.__ Enable Oculus Link.

### Set up the Unreal Engine
__1.__ Navigate to Carla_XR\Unreal\CarlaUE4, double click `CarlaUE4.uproject` to launch the Unreal project.

__2.__ The Oculus link must be enabled before starting the Unreal Engine.

__3.__ The Oculus app must show active connection before starting the Unreal Engine.

__4.__ Navigate to “Content” – “Carla” – “Maps” and select the map(in bottom left of Unreal Engine) after launching the project.

__5.__ There are 3 scenarios being adjusted for this project, which are Rural(Town07), City(Town10HD), and Highway(Town05).

### Set up the Flask Server
__1.__ Open a new command window and navigate to directory `G29/test`.

__2.__ Run the server:
```sh
python angle_sim.py
```

__3.__ The server must be running before executing any simulation.

### Set up the G29 Wheel
__1.__ Open a new command window and navigate to directory `G29/test`.

__2.__ Run the server :
```sh
nodepython angle_phy.jspy
```

__3.__ The wheel script must be running before executing any simulation

### Set up the Scenario Demo for VR
__1.__ Navigate to `Carla\PythonAPI\scenes`

__2.__ Click play on the Unreal scene

__3.__ Select VR Mode using spacebar

__4.__ Run the script

__5.__ Always close the Python script before exiting Unreal scene

## Run the MR simulation

Most procedures for running the MR simulation is the same as VR. Instead of using Oculus Link, you should compile the Unity project under `Unity\CARLAUnityMR` folder as `Apk`, and install it on Quest2.

### Set up the Scenario Demo for MR
__1.__ Navigate to `Carla\PythonAPI\scenes`

__2.__ Click play on the Unreal scene

__3.__ Open the compiled `CARLAUnityMR` App on Quest2

__4.__ Open `NDI to Spout.exe` under `SPOUTtoNDI\bin`

__3.__ Select MR Mode using spacebar

__4.__ Run the script

__5.__ Always close the Python script before exiting Unreal scene

Although MR is implemented, the result is undesireable.

### Calibration

In Unreal project, type init in the top right search box. Click on Level Initializer. There are 3 offsets: X, Y Z . Change Z Increase for higher, decrease for lower.



