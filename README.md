<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com/results?search_query=Azure+Virtual+Machines%2C+Wireshark%2C+and+Network+Security+Groups)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Observe ICMP Traffic
- Configuring a Firewall [Network Security Group]
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img width="830" alt="image" src="https://github.com/user-attachments/assets/02c2eb09-29f7-4060-957f-33e540662b6b" />


</p>
<p>
(Observe ICMP Traffic)
If using Mac, install Microsoft Remote Desktop
Use Remote Desktop to connect to your Windows 10 Virtual Machine
Within your Windows 10 Virtual Machine, Install Wireshark
Open Wireshark and start packet capture
Within Wireshark, filter for ICMP traffic only
Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM
Observe ping requests and replies within WireShark
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
</p>
<br />

<p>
<img width="731" alt="image" src="https://github.com/user-attachments/assets/70b5b8d7-f79a-4239-9775-415aec1acc74" />

</p>
<p>
(Configuring a Firewall [Network Security Group])
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
Stop the ping activity
</p>
<br />

<p>
<img width="665" alt="image" src="https://github.com/user-attachments/assets/a24ce5d9-c372-45e8-b710-7c2637e4922a" />
</p>

<p>
(Observe SSH Traffic)
Log back into the windows-vm
Back in Wireshark, start a packet capture up
Filter for SSH traffic only
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
Open PowerShell, and type: ssh labuser@<private IP address>
Then open PowerShell and then type ssh labuser or the user name you used 
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
Exit the SSH connection by typing ‘exit’ and pressing [Enter]
</p>
<br />

<p>
<img width="727" alt="image" src="https://github.com/user-attachments/assets/006fc0ec-82c8-48d6-aa0f-5d0c30c04361" />
</p>

<p>
(Observe DHCP Traffic)
Back in Wireshark, filter for DHCP traffic only
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line
Open PowerShell as admin and run: ipconfig /renew
Observe the DHCP traffic appearing in WireShark
</p>
<br />

<p>
<img width="728" alt="image" src="https://github.com/user-attachments/assets/d646fb98-2872-45fd-b806-5cffe4071a3a" />
</p>
<p>
Observe DNS Traffic)
Back in Wireshark, filter for DNS traffic only
From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
Observe the DNS traffic being show in WireShark
</p>
<br />

<p>
<img width="728" alt="image" src="https://github.com/user-attachments/assets/0016efca-e365-415d-a255-a51d97eacd74" />
</p>

<p>
(Observe RDP Traffic)
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted
</p>
<br />
