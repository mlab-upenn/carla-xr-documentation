## Server and Client on Two Machines
By default, Carla server and client run on the same machine. However, it has the ability to seperate the
server and client as indicated [here](https://carla.readthedocs.io/en/stable/connecting_the_client/).
In the Virtual Reality environment, it might be desirable to seperate the host and the client to allow each
machine run at a smooth state.

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

### Step 3: Configure Unreal Engine
Inside the UE4 Editor, on the top tool bar, click __Edit__ > __Project Settings__. Under __Plugins__, find __TCP Messaging__. 
Set the Listen Endpoint to be `192.168.1.20:2000`. 

### Step 4: Configure PythonAPI
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

### Step 5: Flask Server
If the above steps were implemented correctly, the Flask server should simutaneously host two sites at
`127.0.0.1:5000` and `192.168.1.20:5000`. However, if the data request fails, manually check these sites
in your browser.

