<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 11
- Ubuntu Server

<h2>High-Level Steps</h2>

- Creating a resource group with Microsoft Azure
- Set up a windows Virtual Machine and A Linux Virtual Machine.
- View ICMP traffic
- Configure a Firewall
- Observe SSH traffic, DHCP traffic, DNS traffic and RDP traffic.

<h2>Actions and Observations</h2>
<p>
  Start off with signing up with <a href="https://azure.microsoft.com/en-us">Microsoft Azure</a> and navigate to the Resource groups tab and get that created, this will be contain the Windows and Linux VMs. 
  <p align="center"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/Screenshot%202026-07-01%20183914.png"></p>
  Next, Navigating to the Virtual Machines tab you can start creating both virtual machines, these will be under the same subscription, in the same resource group, and in the same virtual network. (creating the Virtual machines can automatically set up the virtual network)
  <p align="center"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/Screenshot%202026-07-01%20184259.png"></p>
  Using the settings that you decicde to set up with both virtual machines should end up created and be able to be accessed.
  <p align="center"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/Linux%20VM.png"></p>
  <h3>Wireshark and viewing Ping traffic.</h3>
  Start off by connecting to the windows VM, open up the Remote Desktop Connection application, enter the IP of the windows VM and connect to the machine nand sign into the device using the chosen username and password. Once signed in start installing <a href="https://www.wireshark.org/download.html">Wireshark.</a>
  <p align="center"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/Install%20and%20run%20Wireshark.png"></p>
  After starting wireshark it will begin showing all the traffic going through the device, you can the begin filtering out specific type of traffic such as ICMP traffic. In this example, the windows VM was sending a ping over to the Linux IP address and gettting a response and wireshark displays that traffic.
  <p align="center"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/ICMP%20filter.png"></p>
  You can use IPConfig /all in the command prompt to view the MAC address and compare this with the results shown in wireshark. Since this is viewing one of the replies rather than a request this is showing the destination as the Windows device and the source as the Linux device.
  <p align="center"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/view%20device%20MAC.png"></p>
  <h3>Set up a firewall and monitor pings</h3>
  Back in Azure go to the Linux VM and navigate to the Network Settings, from here set up inbound security rules. Here will block all ping requests so the Windows VM will no longer be be able to ping the device.
  <p align="center"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/Firewall%20block%20ping.png"><img src="https://github.com/JakeMandeville/course-pictures/blob/main/Virtual%20Machines/Ping%20denied.png"></p>
<br />
