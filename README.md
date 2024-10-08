<h1>Banking Networking Project</h1>
This banking network project I will be using CISCO Packet Tracer to demostartes networking knowledge and practical hands on skills that can be used in any industry/enterprise. This project will show how different host devices are configured to different access points; distribution layers, core layers; servers and are able to communicate with one another. The project will be networked to maintain redundancy which will allow host devices to communicate with other devices in the network if one goes down as well as port security measures keep the transfer of data, device configuration and port accessibility secured. This project focuses the implementation of Vlans, Inter-Vlans, Port Security, Network Topology, Wireless Configuration, Trunking, DHCP server configuration (Static), DNS Service, IP configuration (Static and Dynamic), Routing (OSPF) and Switching (Access and Trunk). 
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

<h3>Distribution layer and Core Layer  (Layer 3 Switches & Routers)</h3>
<br>1. First we will enable the switch in privilege access mode. We then will configure the terminal using command "conf t"

<br>2. we will then give the layer 3 switch and routers the appropriate hostname and a banner message.

<br>3. We will then give the switch a password for console configuration

<br>4. we will then set up the L3 switch and router for SSH access 

<br>5. We will then give the devices a no ip domain lookup with an enable password and service password encryption. Then save it with do wr. 

<br>![Screenshot (130)](https://github.com/user-attachments/assets/a8e2065c-e8c5-447b-833b-1cd40914ff9d)

<br>![Screenshot (131)](https://github.com/user-attachments/assets/e0a1eecb-e875-473d-bc75-20252a019a3e)

<hr>

<h2>Trunk and Access port-security</h2>
<br>1. We will begin with connecting the Layer 2 switches from each department to each of the Layer 3 switch on their respective sides. Go into the CLI of the L2 swithc for the Mgt department. The interface in which will be the trunk ports for this device to the L3 device will be fa0/1 and fa0/2 we can use this range in our CLI. We will then turn this switch port mode into a trunk

<br>2. Here we will take our int range in fa0/3-24 for all device to connect to the switch in this department. We will then configure these interface to be access ports for the respectful vlan for each department. In the Mgt department it will be Vlan 10. We then will apply switch port security to a max. of 2 devices, with mac address being obtain through sticky mode (dynamically obtained).We will then implement a shutdown violation for the port security. Then save with do wr command. 

<br>3. We will continue these same commands but ensuring that we change the vlan for each department. We should be able to using the same interface ranges.

<br>![Screenshot (132)](https://github.com/user-attachments/assets/d1c0200f-cb1c-4c69-81ad-ec8f5d78fd0c)

<br>![Screenshot (133)](https://github.com/user-attachments/assets/1420b3bf-a98f-42ae-891d-cdf74821b961)

<br>![Screenshot (134)](https://github.com/user-attachments/assets/f066b155-d30e-4ae5-b2ee-c23975c945c4)

<hr>
<h2>IP addressing</h2>
<br>1. Our base Network address will be 192.168.10.

<br>2. We will now order the address for each department respectfully: Department: Network Address, Subnet Mask. Host Address Range, Broadcast Address and the Vlan it belongs to. 

<br>Managment: 192.168.10.0, 255.255.255.192/26, 192.168.10.1 - 192.168.10.62, 192.168.10.63, VLAN 10

<br>Research: 192.168.10.64, 255.255.255.192/26, 192.168.10.65 - 192.168.10.126, 192.168.10.127,VLAN 20

<br>Human Resource: 192.168.10.128, 255.255.255.192/26, 192.168.10.129 - 192.168.10.190, 192.168.10.191, VLAN 30

<br>Marketing: 192.168.10.192, 255.255.255.192/26, 192.168.10.193 - 192.168.10.254, 192.168.10.255, VLAN 40

<br>Accounts: 192.168.11.0, 255.255.255.192/26, 192.168.11.1 - 192.168.11.62, 192.168.11.63, VLAN 50

<br>Finance: 192.168.11.64, 255.255.255.192/26, 192.168.11.65 - 192.168.11.126, 192.168.11.127, VLAN 60

<br>Logistics: 192.168.11.128, 255.255.255.192/26, 192.168.11.129 - 192.168.11.190, 192.168.11.191, VLAN 70

<br>Customer: 192.168.11.192, 255.255.255.192/26, 192.168.11.193 - 192.168.11.254, 192.168.11.255, VLAN 80

<br>Guest: 192.168.12.0, 255.255.255.192/26, 192.168.12.1 - 192.168.12.62, 192.168.12.63, VLAN 90

<br>Admin: 192.168.12.64, 255.255.255.192/26, 192.168.12.65 - 192.168.12.126, 192.168.12.127, VLAN 100

<br>IT: 192.168.12.128, 255.255.255.192/26, 192.168.12.129 - 192.168.12.190, 192.168.12.191, VLAN 110

<br>ServerRoom: 192.168.12.192, 255.255.255.192/26, 192.168.12.193 - 192.168.12.254, 192.168.12.255, VLAN 120

<br>3. We will not give the network address between the routers and L3 switches. The base network is 10.10.10.0. Picture provided will show what network address goes to each interface. There are 14, Network Address, SubnetMask (all same), Host address Range, Broadcast address.

<br>10.10.10.0, 255.255.255.252, 10.10.10.33 - 10.10.10.34, 10.10.10.35

<br>10.10.10.4, 255.255.255.252, 10.10.10.37 - 10.10.10.38, 10.10.10.39

<br>10.10.10.8, 255.255.255.252, 10.10.10.41 - 10.10.10.42, 10.10.10.43

<br>10.10.10.12, 255.255.255.252, 10.10.10.45 - 10.10.10.46, 10.10.10.47

<br>10.10.10.16, 255.255.255.252, 10.10.10.49 - 10.10.10.50, 10.10.10.51

<br>10.10.10.20, 255.255.255.252, 10.10.10.53 - 10.10.10.54, 10.10.10.55

<br>10.10.10.24, 255.255.255.252, 10.10.10.33 - 10.10.10.34, 10.10.10.35

<br>10.10.10.28, 255.255.255.252, 10.10.10.37 - 10.10.10.38, 10.10.10.39

<br>10.10.10.32, 255.255.255.252, 10.10.10.41 - 10.10.10.42, 10.10.10.43

<br>10.10.10.36, 255.255.255.252, 10.10.10.45 - 10.10.10.46, 10.10.10.47

<br>10.10.10.40, 255.255.255.252, 10.10.10.49 - 10.10.10.50, 10.10.10.51

<br>10.10.10.44, 255.255.255.252, 10.10.10.53 - 10.10.10.54, 10.10.10.55

<br>10.10.10.48, 255.255.255.252, 10.10.10.33 - 10.10.10.34, 10.10.10.35

<br>10.10.10.52, 255.255.255.252, 10.10.10.37 - 10.10.10.38, 10.10.10.39

<br>![Screenshot (135)](https://github.com/user-attachments/assets/816cf2ea-1810-4677-ae42-0d74b0dfd5b6)


<h2>Switchport mode between L2 and L3 switches</h2>
<br>1. We will find the gig interface for all the connection made from the switch ports of each department to the L3 switches. Which will be gig1/0/3 - gig1/0/8. We then will include this command as a range in the L3 switch, change to "switchport mode trunk", exit and "do wr" to safe the configuration in the CLI of each L3 switch. 

<br>![Screenshot (136)](https://github.com/user-attachments/assets/8faa647d-fc7f-4538-96b4-d7b399c0cdce)

<br>![Screenshot (137)](https://github.com/user-attachments/assets/b97d5045-69ca-476c-a1f7-7bb51aa1f39f)


<br>2. We will then go into the L3 switch and make the layer 2 port to be a layer 3 interface, then assign IP address to the interface. in conf terminal > int range gig1/0/1-2 > no switchport > do wr

<br>3. We then will give the L3 switch an IP address and subnet mask based on the networking address from earlier for each interface. 

<br>![Screenshot (138)](https://github.com/user-attachments/assets/69075356-f32c-4f3a-8fca-965da42402b2)


<hr>
<h2>Configure IP address to Routers</h2>

<br>1. We will take the interface of our router, for example gig0/1 on the 10.10.10.3/30 network. We will then use IP address 10.10.10.2 in our configuration becuase we already used 10.10.10.1 for the L3 switch. The subnet will remain the same from last time. 

<br>2. for the connection the the router on floor 4, it will be the same  type of configuration with the next ip address 10.10.10.29 with the same subnet on gig0/0

<br>3.For the connection with the serial port we will use the port with the clocked se port. We will use that interface and apply the IP address on it as well as the clock rate of 64000. Note, ports without the se do not need a clock rating After we will do wr and continue to configure the remaining routers. 

<br>![Screenshot (139)](https://github.com/user-attachments/assets/4e918b2b-cbc5-4132-b8b5-1b8600e4fe75)

<h2>OSPF the Routers and Layer 3 switches</h2>

<br>1. We will first start with going to a router. We will then go into the CLI of the router and enter the command line "router ospf 10". We will then  use command "network (each individual network ip address connected to it) 0.0.0.3 area 0. We will do this for each router and do wr after each. 

<br>![Screenshot (140)](https://github.com/user-attachments/assets/184a71f6-c5bf-4dda-bf4b-57c4eac71209)

<br>2. We will continue to go to the Floor 1 L3's CLI and input  command ip routing, from here we will continue as we did in the previous instruction and apply the network to the two routers it is connected to 10.10.10.0 and  10.10.10.8 with a 0.0.0.3 and area 0. We will then connect to the 6 other networks it is connected to from each department with their respected IP address with a  0.0.0.63 with the same area. We will continue this method with all the other switches with their respected 8  network connections finishing each with do wr to save the configuration.

<br>![Screenshot (142)](https://github.com/user-attachments/assets/1bc15aa1-2a8f-493c-a799-0a9d2c1ef332)


<hr>
<h2>Configure Servers Statically</h2>

<br>1. We first want to configure the IP address of our server. We will go into the Desktop of the server and input an IPv4 address, Subnet Mask and Default Gatewary for each server. Our DHCP ip address will be 192.168.12.196, EMAIL ip address will be 192.168.12.197, HTTPS Server ip address  will be 192.168.12.198. Our Subnet and Default Gateway will be 255.255.255.192 and 192.168.12.193. 

<br>![Screenshot (143)](https://github.com/user-attachments/assets/3e6bbf03-97ee-4f14-9424-8d201b65957d)

<br>2. (DHCP): We want to go to our DHCP server and navigate to our services tab. We will then create a pool for each of the departments. Click on DHCP and turn on service. We will give each department a pool name, default gateway , a starting IP address and a maximum number of users. In the example of our Mgt-Pool we use a default gatway 192.168.10.1 , start the ip address at 192.168.10.6 (skip every 5 from the gateway) with a max of 60 users. We then add it to the server (Note the max user may change to 58, that is okay)

<br>![Screenshot (144)](https://github.com/user-attachments/assets/88ba533d-b999-4447-83ca-886addb4fcde)

<hr>
<h2>Inter-VLAN routing for L3 Switches and IP DHCP helper addresses</h2>

<br> We fisrt want to creat the vlans 10-60 on the Floor1 layer3 switch. We do so by configuring the terminal and entering the vlans. We will "do show start" to see the names of the vlan to verfiy their creation. 

<br>We now will enter "int vlan 10" in the CLI command line > no shutdown > ip helper-address 192.168.12.196. We will not have a helper address for vlan 120 as they are the server in which we gave a IP address statically. Continue this same proccess on both side changing Vlan numbers and IP as needed. 

<br>![Screenshot (152)](https://github.com/user-attachments/assets/fcf60a81-8c71-43fa-af48-1e2bed13387d)

<hr>
<h2>Applying DNS server, testing connection and configuration</h2>

<br>1. We will test to see if the DHCP server is working as well as to see if it applys a dynamic ip address to our devices when it is in this statues. Go to each PC , click on Desktop > IP configuration > DHCP (button)... DHCP request successful should appear. If not there may be a VLAN configuration error in which you will need to go back into each L3 switch and make sure every VLAN and IP address applied to that L3 switch is configured. 

<br>![Screenshot (147)](https://github.com/user-attachments/assets/f9644188-9e2c-45bb-9235-d682fb7ace4b)


<br>2. We will first want to find our DHCP server IP address in the Desktop > IP configuration. We will then navigate to the DHCP tab under Services within the DHCP server. We will then apply the DNS server IP address to each of the pools we created and click save. Notice when you go into one of the PC devices the DNS server name will appear. 

<br>![Screenshot (148)](https://github.com/user-attachments/assets/fd26945b-fc4a-4adf-aec8-d3ab7ac2ebb1)


<br>![Screenshot (149)](https://github.com/user-attachments/assets/4ec7fccf-8fa0-448d-8a86-4296f9a8e827)


<br>3. We will then navigate to DNS tab on the DHCP server and turn the DNS service on, We will give the DNS a name and apply the same ip address from our DHCP server and click add and save. We will then go to Desktop > Website and type in the name of the DNS we just created and it should take us to our website.

<br>![Screenshot (151)](https://github.com/user-attachments/assets/2d97c47d-deb3-4945-b593-ae915c7fe613)


<br>![Screenshot (150)](https://github.com/user-attachments/assets/f9013f09-fd59-4220-b9e4-8d4b0b342e96)

<hr>

<h2> Wireless network configurations (Access Point) and other verifications </h2>

<br>1. For this demostration of configuring a access point we will click on the FIN-AP. We will then go to config > port 1 > and give the device a wifi name (Finance-Wifi) as well as a WPA2-PSK password (Finance@2024). We will then grab a laptop from our end point devices. We will need to turn off the pc, apply a wireless card (WPC300N), then turn it back on. We will then go to Desktop > wireless connection > connect > Refresh and find out Finance-Wif. We will connect and apply our password which will then connect to our access point. We will then find out laptop ip address and ping it from anothe pc in any network to make our connection (note the first packet will fail but the other should ping; try).

<br>![Screenshot (153)](https://github.com/user-attachments/assets/4f944c85-8623-4a81-b7f9-686e52327812)

<br>![Screenshot (154)](https://github.com/user-attachments/assets/a0debf2f-13c7-4357-9be0-db085212f817)

<br>![Screenshot (155)](https://github.com/user-attachments/assets/934135ab-79b3-4e6d-ac09-6812e4ae7726)

<br>![Screenshot (156)](https://github.com/user-attachments/assets/fb57ea92-5163-4ec7-8161-b09cd0c5c5fa)


<br>2. Now try pinging other PCS across networks. 

<br>![Screenshot (157)](https://github.com/user-attachments/assets/89b5fbad-2a0d-4598-9bf6-6afd25ab4dc8)

<hr>

<h2>Reference</h2>

<br>https://www.youtube.com/watch?v=NLMqmaBvD8Q




