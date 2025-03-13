# Azure VM Network Analysis - Part 4 - Network Protocols
<h2>Description</h2>
In this guided lab, we will analyze network traffic using Wireshark and PowerShell while experimenting with various network protocols, including SSH, DHCP, DNS, and RDP.
<br />
<br />
<p align="center">
<img src="https://i.imgur.com/1JmaYVn.png" alt="Traffic Examination"/>
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop 
- PowerShell 
- Network protocols (SSH, DHCP, DNS, RDP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro, version 22H2
- Ubuntu Server 22.04 LTS

<h2>High-Level Steps</h2>

- Step 1: Filter for SSH traffic
- Step 2: SSH into the Linux Virtual Machine 
- Step 3: Observe SSH traffic 
- Step 4: End the SSH connection
- Step 5: Filter for DHCP traffic 
- Step 6: Renew the Windows Virtual Machine IP address 
- Step 8: Observe DHCP traffic
- Step 9: Filter for DNS traffic 
- Step 10: Initiate a DNS lookup and observe traffic
- Step 11: Filter for RDP traffic and observe
- Step 12: Cleanup the Lab
  
  

<h2>Actions and Observations</h2>

<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="https://i.imgur.com/86ntNVt.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Back in Wireshark, start a new packet capture and filter for SSH traffic by typing "ssh" and then pressing "Enter" in the search bar. Let it run.
</p>
<br />




<h3>Step 2: SSH into the Linux Virtual Machine</h3>

<p>
<img src="https://i.imgur.com/HEhw5bS.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-In PowerShell, type: "ssh Labuser007@10.0.0.5" (the Linux VM private IP address may be different for you) and press "Enter". You will already notice SSH traffic being generated in Wireshark.

-Type "yes" and press "Enter" to continue connecting.
 You will then be prompt to enter a password, use the one that you created in Azure for the Linux VM and press "Enter". (When you type your password, nothing will appear. This is normal, it's for security purposes. Your input will still process.)

-You should notice a new prompt which looks different then what we normally see  in Windows PowerShell (or cmd). This confirms that we are remotely connected to the Linux VM via SSH.
</p>
<br />




<h3>Step 3: Observe SSH traffic</h3>

<p>
<img src="https://i.imgur.com/LyN2qN0.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Back in Wireshark, inspect SSH traffic and the information provided by the packet capture (source IP, destination IP, source port, destination port, MAC addresses, protocols).  

  -You should also try out other Linux commands (hostname, pwd, id, ifconfig, toucht, ls, rm, etc). 
Every time you input something, you will notice SSH traffic occurring in Wireshark.  
</p>
<br />




<h3>Step: 4 End the SSH connection</h3>

<p>
<img src="https://i.imgur.com/rTEFK4Y.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-To end the SSH connection, go back to PowerShell and type "exit" and then press "Enter". This will automatically end the SSH session and reconnect to the Windows VM. 
  
-To confirm this reconnection to the Windows VM, use the command: "hostname" (this indicates the name of the device you are currently connected to). 
</p>
<br />




<h3>Step 5: Filter for DHCP traffic</h3>

<p>
<img src="https://i.imgur.com/Cr1X7Ps.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-In Wireshark, restart a new packet capture and filter for DHCP traffic by typing "dhcp" in the search bar. Let it run.
</p>
<br />





<h3>Step 6: Create a DHCP script</h3>

<p>
<img src="https://i.imgur.com/VDrWVIT.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Before renewing the Windows VM's IP address, we have to create a script that will allow us to release and renew the IP address in a single process instead of running these commands one after the other. This will prevent our Windows VM from completely being disconnected from the Virtual Network, and ensure that Wireshark captures the full DHCP exchange.  

-To create the script, open a new window in Notepad and type "ipconfig /release" on the first line, and "ipconfig /renew" on the second line. 

-Type "Ctrl s" and save it as a Batch file (ex: DHCP.bat) in a location that is easily accessible.
</p>
<br />





<h3>Step 7: Renew the Windows Virtual Machine IP address and observe DHCP traffic</h3>

<p>
<img src="https://i.imgur.com/CNQCGRg.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Back in PowerShell, run the previously created Batch file with the command: "./downloads/DHCP.bat" (your Batch file name may be different). Your VM will disconnect for a couple seconds and then reconnect automatically. 

-Even though the DHCP script process worked, you will notice that your Windows VM has been reassigned the same IP address as before. This is normal, Azure configures a DHCP reservation for each active VM to prevent IP address exhaustion and disruption.

-In Wireshark, you should be able to observe the normal process of the Windows VM  releasing its IP address and acquiring a new one through DHCP.
This process is also referred to as DORA (Discover - Offer - Request - Acknowledge). It starts with a discovery, which in this case involves the Windows VM broadcasting a message to look for (Discover) the DHCP server. The DHCP server will then respond (Offer) with an available IP address. Upon receiving the offer from the DHCP server, the Windows VM will ask (Request) to be assigned the offered IP address. And finally, the DHCP server will acknowledge (ACK) the request for the Windows VM new IP address.
</p>
<br />





<h3>Step 8: Filter for DNS traffic </h3>

<p>
<img src="https://i.imgur.com/GcoPRmg.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-In Wireshark, restart a new packet capture and filter for DNS traffic by typing "dns" in the search bar. Let it run.
</p>
<br />





<h3>Step 9: Initiate a DNS lookup and observe traffic</h3>

<p>
<img src="https://i.imgur.com/y9Ayn8y.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Back in PowerShell, type "nslookup www.professormesser.com" (or any other website that you want to check) and inspect the results. What do you think will happen if you try to connect to a website with just the IP address?

-In general, most websites will show an error message/default page when accessed via their IP address. Thus, users must typically connect to a website using the domain name.

-Additionally, observe the results in Wireshark, you should notice a spam of traffic occurring. This is due to multiple network processes occurring in the background to load the website. By now, you should feel more comfortable locating basic information in Wireshark.
</p>
<br />





<h3>Step 10: Filter for RDP traffic and observe</h3>

<p>
<img src="https://i.imgur.com/DWUJlPL.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Lastly, go back to Wireshark and restart a new packet capture.

-Before filtering for RDP traffic, what results do you expect to see; a spam of traffic or just a few lines of packets? 

-Type "tcp.port == 3389"  and then press "Enter" in the search bar to filter for RDP traffic. Is the result what you expected? 

-Since we are currently connected to our Windows VM via RDP and a lot of communication (mouse movements, keyboard inputs, screen updates) are occurring between the RDP connection (client) and the Windows VM (server), you should expect a continuous stream of packets, rather than just a few lines of packets.
</p>
<br />





<h3>Step 11: Cleanup the Lab</h3>

<p>
<img src="https://i.imgur.com/nEM8EBQ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Close all opened windows and turn off your Remote Desktop connection.
</p>
<br />



<p>
<img src="https://i.imgur.com/Alt4mSy.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Back in Azure, type "Resource groups" in the search and delete the Resource Group created at the beginning of this lab (if you see a second one, delete it too). Your VMs will be deleted subsequently because they are part of the Resource Group.
</p>
<br />




<p>
<img src="https://i.imgur.com/s3gHEyF.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
-Verify Resource Groups deletion to ensure that no resources are left behind, preventing unnecessary costs and resource consumption. 

                         I hope that you found this whole guided lab informative. Thank you! :)
</p>
<br />

