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

<br>1. Router 2911 will be used for each router on each floor. Each router is given "Floor-(1-4) Router". We then will connect each router with a Serial DCE cord, but we first must must go into each individual router, turn it off, place the "HWIC-2T" module into the back of the router and turn the router back on.

<br>![Screenshot (119)](https://github.com/user-attachments/assets/5c9857b4-c4e8-4f91-a37b-308c2b965283)

<br>2. We will then connect the Serial DCE cord from one router to another in the serial ports. We then will connect Floor-1 Routers Gig Ethernet0/0 to Floor-4 Routers Giga Ethernet 0/0 with a Copper Cross Over cord, as well as do the same for Floor-2 to Floor-3. This will help maintain redundancy if 1 router goes down this mesh topology between the routers will help maintain a connection. 

<br>3. We will then use the recommended connection to connect our L3-Switch from each floor to it respected floor and the one nearest to it. This will be a Copper-Straight through cord. The connection will be as such. Floor-1 L3 Switch's Gig 1/0/1 will connect to Floor-1 Routers Gig 0/1 interface; Floor-1 L3 Switch will then be connected to Floor-2 Routers interface (any Gig interface available). We will continue to do so for each of the other L3 Switches on each floor

<br>4. We will then connect each of the access layer switches for each department to both L3 switches on there respected side using the copper cross-over cord ensuring that each interface is connected in chronological order. 1 Access switch should have fa 0/1 and 0/2 connected to each LW switch on its side respectfully, where as each L3 Switch should be connected to each Access switch (Gig 1/0/3 -Gig 1/0/8).

![Screenshot (120)](https://github.com/user-attachments/assets/ac826fdf-380d-4bfb-b02a-9a6b48541252)


<br>5. We now will grab 1 PC, Printer and Access point and use the recommended cord ( Copper Straight Through) and connected each of the three device to their respected switch for each floor (keep in mind of the interface you connect after using the reccommended cord option).We will have three server which we will name DHCP Server, Email Server and HTTPS Server connected to the 4th floor switch. We will name each host device connected to each switch with its assigned switch (Floor-1 MGT-SW > MGT PC,AP and Printer)

<br>![Screenshot (124)](https://github.com/user-attachments/assets/f84fe75f-9ab8-4288-a5a9-0032e11ccb28)
<br>![Screenshot (125)](https://github.com/user-attachments/assets/a3597357-49d3-4ec4-ad28-1045e67b4b59)


<br>6. We will now need to turn on our Routers and L3 Switch so their connection can be made. We will navigate to any router and turn the port status of each of the 5 interfaces connected to "on". This can also be done in the CLI, by navigating to the to the respect #interface then typing the command #no shutdown then typing #do wr to save the change.

<br>![Screenshot (121)](https://github.com/user-attachments/assets/589c38b0-496b-47c3-a69c-745f9ea670db)

<br>7. We will then go to each of our L3 switches and apply a AC power supply to turn on the devices to make its connections to the other device connected to them.

<br>![Screenshot (123)](https://github.com/user-attachments/assets/aa73a042-191a-4462-8c53-9f0f0fb1bffd)

<br>8. We will now border off our devices to their respected floors and departments for later segementation. VLAN 10 - MGT, VLAN 20-RS, VLAN 30-HR, VLAN 40 -MKT, VLAN 50 -ACC, VLAN 60 - FIN, VLAN 70 - LOG, VLAN 80 - CC, VLAN 90 - GST, VLAN 10 -ADMIN, VLAN 110 - IT, VLAN 20 -SVR

<br>![Screenshot (127)](https://github.com/user-attachments/assets/eabe6eb6-b3f1-4628-893a-4750f5de3674)

<hr>

<h2>Configurations /Simulation</h2>
<h3>Access Layer (Layer 2 switches)</h3>
<br>1. On the Floor 1 Management switch we will navigate to the "CLI" tab. We will then enable privilege access mode by using the "en" command. Then once in privilege mode we will then use the configure terminal command, "conf t" to begin configuring the switch.

<br>2. We will now give the switch a hostname and a banner message. We will do so using the command "hostname F1-Mgt-SW" and banner motd #This is Floor1-Mgt switch#.

<br>3. Now we will give the switch a security password that needs to be submit in order to access the configuration of the device. We will do so using the commands in order. line console 0, password cisco, login, exit

<br>4. We will also give the switch a remote password for login as well. We will use the commands in this order. line vty 0 15, password cisco, login, exit.

<br>5. Lastly, we will input the commands so that the switch will not misinterpert domain name and look up those that do not exist. We will also enable a password with to enable privilege access and encypt all our password. We will finish by saving our configuration by using the "do write" commands. Configure these commands in this order. no ip domain-look, enable password cisco, service password-encryption, do wr. 

<br>6. These commands will be applied to all layer 2 switches with proper naming convictions by writing them in note pad, copying and pasting in the appropriate switch. 

<br>![Screenshot (129)](https://github.com/user-attachments/assets/47dc034a-55e4-4f85-a90b-edfed7024877)


<br>![Screenshot (128)](https://github.com/user-attachments/assets/32ae2906-f718-499b-ac6c-94af2fd76344)

<hr>

<h3></h3>


