# Azure VM Network Analysis - Part 4 - Network Protocols Traffic Analysis

In this guided lab, we will analyze network traffic using Wireshark and PowerShell while experimenting with various network protocols, including SSH, DHCP, DNS, and RDP.

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
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />




<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />





<h3>Step 1: Filter for SSH traffic</h3>

<p>
<img src="" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

