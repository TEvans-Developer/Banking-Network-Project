<h1>Banking Networking Project</h1>
This banking network project I will be using CISCO Packet Tracer to demostartes networking knowledge and practical hands on skills that can be used in any industry/enterprise. This project will show how different host devices are configured to different access points; distribution layers, core layers; servers and are able to communicate with one another. The project will be networked to maintain redundancy which will allow host devices to communicate with other devices in the network if one goes down as well as security measure implement to keep the transfer of data and its accessibility secured.
<hr>

<h3>Setup</h3>
<br><i>The bank will be networked for four floors. Each floor will have a router and layer 3 switch. Each floor will have three different departments for a total of 12 departments.
  
<br>The bank will have 20 host-devices and 4 printers in our Management, Research, Human Resources, Marketing, Accounting, Finance, Logistics & Store and Customer Care departments. 

<br>Our Guest Area on Floor 3 will have 40 host device and 2 printers.

<br>The banks Administration and IT department will have 20 host device each and 2 printers on the 4th floor. The 4th floor will also host the Server room, which will have 2 admin pcs and 3 servers ( DHCP,HTTP and EMAIL)</i>

<br> Each department will being hosting wired and wireless devices, so there will be a wireless network. 

<br> Each device will habve an IPv4 address automatically from the deddicated DHCP server in the server room.

<br> SSH will be configured in all routers for remote login, the routers will also use OSPF as the routing protocol to advertise routes. 

<h3>Configuration of the devices***</h3>
<i>Devices will have one or the other, Hostnames, Line Console and VTY passwords, Banner messages and disabled domain IP lookup</i>

<h3>Vlan for each department***</h3>
<i>Each department will have a VLAN (Vlan 1, 10, 20 ...etc.) Where each VLAN will have a different subnetwork. Each subnet will be different based on the number of host in every department. A subnet mask, reusabke IP address range and broadcast address for each subnet will be made.</i>

<h3>Port-security***</h3>
<i> There will be sticky command to obtain MAC address and violation mode for shutdown.</i>

<hr>

<h2>Design Topology.</h2>
Router 2911 will be used for each router on each floor. Each router is given "Floor-(1-4) Router". We then will connect each router with a Serial DCE cord, but we first must must go into each individual router, turn it off, place the "HWIC-2T" module into the back of the router and turn the router back on.

<br>2. We will then connect the Serial DCE cord from one router to another in the serial ports. We then will connect Floor-1 Routers Gig Ethernet0/0 to Floor-4 Routers Giga Ethernet 0/0 with a Copper Cross Over cord, as well as do the same for Floor-2 to Floor-3. This will help maintain redundancy if 1 router goes down this mesh topology between the routers will help maintain a connection. 

<br>3. We will then use the recommended connection to connect our L3-Switch from each floor to it respected floor and the one nearest to it. This will be a Copper-Straight through cord. The connection will be as such. Floor-1 L3 Switch's Gig 1/0/1 will connect to Floor-1 Routers Gig 0/1 interface; Floor-1 L3 Switch will then be connected to Floor-2 Routers interface (any Gig interface available). We will continue to do so for each of the other L3 Switches on each floor

<br>4. We will then connect each of the access layer switches for each department to both L3 switches on there respected side using the copper cross-over cord ensuring that each interface is connected in chronological order. 1 Access switch should have fa 0/1 and 0/2 connected to each LW switch on its side respectfully, where as each L3 Switch should be connected to each Access switch (Gig 1/0/3 -Gig 1/0/8).

![Screenshot (120)](https://github.com/user-attachments/assets/ac826fdf-380d-4bfb-b02a-9a6b48541252)

