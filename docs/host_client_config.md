## Running the VR simulation
### Set up the Oculus Headset
__1.__ Connect your headset to the computer using a USB-C wire and turn on the headset. <br />
__2.__ When prompted, __Allow__ device to access data from the computer. <br />
__3.__ If Guardian is not found, create Guardian using the controller. <br />
__4.__ Turn on Oculus desktop program, go to __device__ and make sure the headset is connected. <br />
__5.__ Enable Oculus Link, use this [video](https://www.youtube.com/watch?v=IQrPiTlsU9I) as a reference. <br />
__6.__ __Important__: Oculus link must be enabled before turning on the Unreal Engine, or you will not be able to click the __Run Simulation__ button.

### Set up the Unreal Engine
__1.__ Navigate to your CARLA project source foler, and then \Unreal\CarlaUE4, double click __CarlaUE4.uproject__ to launch the project. <br />
__2.__ Inside Unreal Editor, navigate to `Content\Carla\Maps` and double click to select the map (Map7 is used by default for the sample PythonAPI). <br />
__3.__ Inside the Unreal Editor, click __>>__ on the top right corner to expand the toolbar, choose __Active Play Mode > VR Preview__. <br />
__4.__ Click __Play__ to start simulation, you should be able to see the animation in your Oculus headset. Select VR Mode using spacebar <br />
__5.__ The first time you play the simulation, UE4 will show a white screen for a few minutes.

### Set up G29 Wheel Server (Optional)
This step is optional. Only do it if you want the automatic wheel turning. You do __NOT__ need to implement this step
to read the wheel input as it is already included in the Pythong script. For further information on implementation, click [here](https://github.com/nightmode/logitech-g29). 

__1.__ Open a new command window and navigate to directory `G29/test`. <br />
__2.__ Start the NodeJS express server by running `node angle_phy.js`. <br />
__3.__ You should be seeing a list of wheel information followed by __wheel ready__. 
If you encounter an error, your wheel might not be connected or your driver is not update to date. <br /> 
__4.__ Make sure the server is running before executing any related python scripts.

### Set up the Flask Server (Optional)
This step is optional. However, not doing it would result in no animation inside the vehicle.

__1.__ Open a new command window and navigate to directory `G29/test`. <br />
__2.__ Start the server by running `python angle_sim.py`. <br />
__3.__ You should be seeing a warning message followed by the server information. <br />
__4.__ Open page __127.0.0.1:5000/get_steer__ in a browser to verify that the server is running.

### Run the Scenario Demo
__1.__ Navigate to `Carla\PythonAPI\VR_Scripts` <br />
__2.__ Run our selected python script using a terminal or an IDE. Some scripts will strictly require the wheel server and/or the Flask server to be running. <br />
__3.__ __Important__: Unreal Engine needs play the VR simulation before executing any Python script. <br />
__4.__ __Important__: Always terminate the Python script before exiting Unreal simulation.

### Driver's View Calibration (Optional)
The view by default it aligned to the driver's seat. However, additional calibration might be needed to adjust the view.
To do this, open a map and type _init_ in the top right search box. Click on __Level Initializer__. Change the offsets _X, Y, Z_
for an adjustment in the absolute position. Currently there is no way to change the orientation. Adjustments can only be made
while the simulation is __NOT__ running.

## Running the MR simulation
Most steps for running the MR simulation is the same as VR. Instead of using Oculus Link, you should compile the Unity project under `Unity\CARLAUnityMR` folder as `Apk`, and install it on Quest 2.

### Set up the Scenario Demo for MR
__1.__ Click play on the Unreal scene <br />
__2.__ Open the compiled `CARLAUnityMR` App on Quest2 <br />
__3.__ Open `NDI to Spout.exe` under `SPOUTtoNDI\bin` <br />
__4.__ Select MR Mode using spacebar <br />
__5.__ Navigate to `Carla\PythonAPI\VR_Scripts` and run the script <br />
__6.__ Always terminate the Python script before exiting Unreal simulation. <br />

__Note__: this implementation runs MR at a low quality and is not recommended to use.


