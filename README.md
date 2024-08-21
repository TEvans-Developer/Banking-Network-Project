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
