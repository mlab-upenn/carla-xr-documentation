## Server and Client on Two Machines
By default, Carla server and client run on the same machine. However, due to the convoluted nature of the
Virtual Reality environment, it is highly recommended that the server and the client being seperated on two
machines. For more information on Carla server and client, check [here](https://carla.readthedocs.io/en/stable/connecting_the_client/).

In our implementation, the server machine is responsible for: hosting Unreal Engine and the Carla project, connecting
the Oculus Quest headset and rendering VR animation. The client machine is responsible for: hosting the Flask server,
controlling the G29 wheel, and running the PythonAPI. For more information, refer to our [Running XR Simulation](run_simulation.md) page.


### Step 1: Connnect Two Machines
Conenct the two machines with an Ethernet cable. Due to enormous data transfer rate, CAT6 and above is required.
An USB-C port with ethernet adaptor is also feasible.

### Step 2: Configure IP Address
* On the server (Unreal Engine) machine, navigate to __Control Panel__ > __Network and Internet__ > __Network and Sharing Center__.
Click __Ethernet__ > __Properties__ > __Internet Protocol Version 4 (TCP/IPv4)__. Manually enter the IP address `192.168.1.21`,
subnet mask `255.255.255.0`, and leave Default gateway as blank. On the bottom, manually enter the Preferred DNS server `8.8.8.8`,
and leave the Alternate DNS server as blank.

* On the client (PythonAPI) machine, navigate to __Control Panel__ > __Network and Internet__ > __Network and Sharing Center__.
Click __Ethernet__ > __Properties__ > __Internet Protocol Version 4 (TCP/IPv4)__. Manually enter the IP address `192.168.1.20`,
subnet mask `255.255.255.0`, and leave Default gateway as blank. On the bottom, manually enter the Preferred DNS server `8.8.8.8`,
and leave the Alternate DNS server as blank.

### Step 3: Configure Unreal Engine (Server)
Inside the UE4 Editor, on the top tool bar, click __Edit__ > __Project Settings__. Under __Plugins__, find __TCP Messaging__. 
Set the Listen Endpoint to be `192.168.1.20:2000`.

Inside the UE4 Editor, on the Content Browser on the bottom, navigate to __Content__ > __CarConfigurator__ > __Car__ > __Blueprints__.
Double click to open __BP_AudiA5_CARLA_V3__. Click __EventGraph__ on the left panel, and drag the blueprint to find __Va Rest Subsystem__
on the top left section. Locate the block __Call URL__, and change the URL from `http://127.0.0.1:5000/get_steer` to `http://192.168.1.20:5000/get_steer`.

### Step 4: Enable Oculus Link (Server)
Connect Oculus Quest 2 headset to the server machine and enable Oculus Link. Verify that the headset
is successfullly conencted in the Oculus desktop application and you are able to run the simulation in the Unreal Carla project.

### Step 4: Configure PythonAPI (Client)
In the PythonAPI script, find one of the following lines 
```sh
client = carla.Client(‘127.0.0.1’, 2000)
```
```sh
client = carla.Client(‘localhost’, 2000)
```
and replace it with 
```sh
client = carla.Client(‘192.168.1.21’, 2000)
``` 
This allows the client to actively look for an outside server
instead of the local machine. Make sure port 2000 is not blocked by some other tasks or the windows firewall.

If a Python script involves posting data to Flask server, you need to find the following line
```sh
url = http://127.0.0.1:5000/set_steer
```

and replace it with
```sh
url = http://192.168.1.20:5000/set_steer
```

__Note:__ You only need the PythonAPI folder on the client machine with related dependencies installed. You do
not need the Carla project source code or the Unreal Engine on the client machine.

### Step 5: Flask Server (Client)
Follow instructions on Flask server from the Running XR Simulation page. If the machines were connected correctly, 
the Flask server should simutaneously host two sites at `127.0.0.1:5000` and `192.168.1.20:5000`. 
However, if the data request fails, manually check these sites in your browser.

### Step 6: G29 Wheel (Client)
Connect G29 wheel to the client machine, and follow instructions as in the Running XR Simulation.
