<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, I observed various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Creating 2 Virtual Machines in Azure
- Connecting to the Microsoft VM with Remote Desktop
- Installing Wireshark
- Examining different protocols and Network Security Groups

<h2>Actions and Observations</h2>

<p>
This first screenshot is where in Microsoft Azure I created 2 Virtual Machines.
<img width="1697" alt="Azure VMs creation" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/b88eb3fa-60d9-4ab2-8ccb-d459849b6902">
</p>
<br />
Here is where I connected to the Windows 10 VM using a Remote Desktop connection.
<img width="1710" alt="RDP-login" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/7c127e3e-a1af-4b42-b518-b492d6fbc8fc">
</p>
<br />
Inside the Windows VM I then downloaded Wireshark, which is a protocol traffic analyzer.
<img width="1710" alt="Wireshark Installation" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/a51e8698-5ff7-4d4f-86cd-41c8534a37a7">
</p>
<br />
I first filtered for ICMP traffic and then used a ping command in powershell to test network connectivity to the Ubuntu VM and Internet by pinging Google.
<img width="1710" alt="ICMP traffic view" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/169850b7-23f2-4a4f-a3bb-19abb753cd10">
</p>
<br />
These two screenshots are of me experimenting with the Network Security Groups of the Ubuntu VM. I disabled incoming ICMP traffic on the firewall of the Ubuntu VM so that the Windows VM cound not receive any ping reply. I then immediately allowed the ICMP traffic again.
<img width="1710" alt="NSG experiment" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/c4dd0a4e-d7b8-4a3d-87fd-5432b52e3f6f">
<img width="1710" alt="NSG experiment -2" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/f2273a83-f087-4853-b7ab-45df0bdea5c0">
</p>
<br />
Filtered for SSH traffic. I spawned the command line for the Ubuntu VM. I tested it by using the Linux commands "uname -a" and "pwd".
<img width="1710" alt="SSH traffic view" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/149a346e-afbd-42e3-908a-75d4c51604aa">
</p>
<br />
Filtered for DHCP traffic. I used the ipconfig /renew command to issue the VM a new IP address.
<img width="1710" alt="DHCP traffic view" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/5c0c352c-71c8-4430-a18a-0b76dfeae9e5">
</p>
<br />
Filtered for DNS traffic. I viewed the IP addresses of www.google.com and disney.com in powershell by using the "nslookup" command.
<img width="1710" alt="DNS traffic view" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/22fda6b3-71e2-4c14-aabf-45688321ccbe">
</p>
<br />
The last protocol traffic I viewed was RDP. You can't tell by the picture but the traffic was continously moving since the connection is live from my physical laptop to the Windows 10 VM.
<img width="1710" alt="RDP traffic view" src="https://github.com/brysonejones/azure-network-protocols/assets/163891519/4f189a02-0e42-481d-8a0a-f3ec67d8ae2d">
