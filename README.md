<p align="center">
  <img width="297" height="65" alt="image" src="https://github.com/user-attachments/assets/499c27ec-8b27-47f7-9f60-c28191276562" />
  <img width="145" height="57" alt="image" src="https://github.com/user-attachments/assets/10050681-339e-406f-906b-0683d42eeb44" />
  <img width="297" height="117" alt="image" src="https://github.com/user-attachments/assets/f3cbff92-dffb-46e0-b8ed-556d7ce170a0" />
</p>

<h1>Network Traffic Analysis Between Azure VMs Using NSGs and Wireshark</h1>

<p> 
This project provides an overview and hands-on lab demonstrating how core network traffic behaves inside a cloud-hosted environment using Microsoft Azure Virtual Machines. The lab walks through creating a Windows 10 VM and an Ubuntu Linux VM inside the same virtual network, installing and using Wireshark to capture traffic, and analyzing how different protocols operate in real time. By using both Windows CMD/PowerShell and Bash on the Ubuntu VM, pinging between VMs, connecting over SSH, renewing DHCP leases, performing DNS lookups, and observing continuous RDP traffic, this project illustrates how ICMP, SSH, DHCP, DNS, and RDP packets move across a virtual network and how Network Security Groups (NSGs) affect communication. This lab builds foundational skills in cloud networking, packet analysis, virtual machine connectivity, and network troubleshooting—key capabilities for IT support, networking, and cybersecurity professionals. 
</p>

<p align="center">
  <img width="815" height="316" alt="image" src="https://github.com/user-attachments/assets/cc38f654-5332-490f-bd8d-7a7d1cb4d412" />
  <img width="732" height="679" alt="image" src="https://github.com/user-attachments/assets/0848e429-cc27-4225-87d9-2630519094b3" />
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Resource Group, Virtual Machines, Virtual Network (VNet), and Subnet)
- Network Security Groups (NSGs)
- Azure Network Watcher
- Remote Desktop (RDP)
- Wireshark (Protocol Analyzer)
- <img align="center" alt="PowerShell Icon" width="20px" src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/powershell-colored.svg" /> PowerShell
- Various Command-Line Tools
- Linux Terminal (Bash)
- ICMP (Ping)
- Secure Shell (SSH)
- DHCP (Dynamic Host Configuration Protocol)
- DNS (Domain Name System

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 24.04

<h2>High-Level Steps</h2>

- Step 1. Create Resources
- Step 2. Observe ICMP Traffic
- Step 3. Observe SSH Traffic
- Step 4. Observe DHCP Traffic
- Step 5. Observe DNS Traffic
- Step 6. Observe RDP Traffic

<h3>Step 1. Create Resources</h3>

<h4>1. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>2. Create a Windows 10 Virtual Machine (VM), and select the previously created Resource Group</h4>

<p>
  <img width="764" height="701" alt="image" src="https://github.com/user-attachments/assets/df689c31-2a50-401d-a1e2-638e2848ed75" />
  <img width="778" height="712" alt="image" src="https://github.com/user-attachments/assets/ab5412c6-25c9-49c4-b222-25724f63b2a8" />
  <img width="776" height="702" alt="image" src="https://github.com/user-attachments/assets/9283a744-535b-4bc7-937c-e17fcb573ca9" />
</p>

<h4>2a. While creating the VM, allow it to create a new Virtual Network (VNet) and Subnet</h4>

<p>
  <img width="771" height="694" alt="image" src="https://github.com/user-attachments/assets/43dd2c17-94c2-4751-9271-9e98241bf059" />
</p>

<h4>3. Create a Linux (Ubuntu) VM</h4>

<p>
  <img width="769" height="697" alt="image" src="https://github.com/user-attachments/assets/8ad69c3d-bd11-404a-b424-89ba20472346" />
  <img width="762" height="637" alt="image" src="https://github.com/user-attachments/assets/128efa86-4f97-41ad-8179-21e3791cc0b7" />
  <img width="770" height="629" alt="image" src="https://github.com/user-attachments/assets/aa0ffa7b-acb8-49cf-8c04-718374e980da" />
</p>

<h4>3a. While creating the VM, select the previously created Resource Group, VNet, and Subnet</h4>

<p>
  <img width="783" height="702" alt="image" src="https://github.com/user-attachments/assets/8b4e905a-8a48-4b91-9d5f-aea7865dbc3f" />
</p>

<h4>4. Use Network Watcher to inspect the Virtual Network and confirm that both VMs are connected to the same VNet and Subnet.</h4>

<p>
  <img width="1027" height="622" alt="image" src="https://github.com/user-attachments/assets/54eb99e3-b1b6-4b6d-bb91-0b3a05f628b3" />
  <img width="1009" height="620" alt="image" src="https://github.com/user-attachments/assets/27ca0d28-8ccc-4773-be0e-d14c683abc73" />
</p>


<h4>4a. Observe our Virtual Network, both NSGs (one for the Windows VM and one for the Linux VM), and both VMs (Windows and Linux) within the RG-Network-Activities Resource Group that we created.</h4>

<p>
  <img width="1327" height="765" alt="image" src="https://github.com/user-attachments/assets/1991320d-2e7d-425d-bd00-3b5478295a2a" />
</p>

<h4>Step 1 Summary</h4>

<p>
In Step 1, we create a Resource Group to organize all of our Azure components. We then deploy a Windows 10 Virtual Machine and allow Azure to automatically create a new Virtual Network (VNet) and Subnet for it. Next, we deploy an Ubuntu Linux Virtual Machine into the same Resource Group and VNet so both machines can communicate over the private network. We used Network Watcher to inspect the Virtual Network and confirm that both VMs are connected to the same VNet and Subnet. Finally, we observe our Virtual Network, both NSGs (one for the Windows VM and one for the Linux VM), and all VMs within the RG-Network-Activities Resource Group that we created.
</p>

<h3>Step 2. Observe ICMP Traffic</h3>

<h4>5. Use Remote Desktop to connect to your Windows 10 Virtual Machine</h4>

<p>
  <img width="619" height="377" alt="image" src="https://github.com/user-attachments/assets/0c2b0759-3342-4349-9023-89716d1eff88" />
</p>

<h4>6. Within your Windows 10 Virtual Machine, install Wireshark</h4>

<p>
  <img width="792" height="586" alt="image" src="https://github.com/user-attachments/assets/4a608f3a-abe2-4f45-bda0-fd6dabcff3cd" />
</p>

<h4>7. Open Wireshark, click "Ethernet", then click the blue shark fin icon to start capturing packets, apply a filter for ICMP traffic only</h4>

<p>
  <img width="743" height="575" alt="image" src="https://github.com/user-attachments/assets/64914628-4462-4553-9528-55e0d28443ca" />
  <img width="743" height="576" alt="image" src="https://github.com/user-attachments/assets/97b127c6-a9fc-4683-a09c-216673a36af1" />
</p>

<h4>8. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM</h4>

<p>
  <img width="1269" height="395" alt="image" src="https://github.com/user-attachments/assets/de61a064-aa2a-4a37-b9cf-2a79672df534" />
  <img width="851" height="699" alt="image" src="https://github.com/user-attachments/assets/e143cfb5-877f-4229-b5b9-9670bea1d674" />
</p>

<h4>8a. Observe ping requests and replies within Wireshark</h4>

<p>
  <img width="773" height="698" alt="image" src="https://github.com/user-attachments/assets/9ac5afd0-839e-4279-b1a9-236bd7e6e50e" />
</p>

<h4>9. From the Windows 10 VM, open PowerShell or Command Prompt, ping a public website (such as www.google.com), and observe the traffic in Wireshark</h4>

<p>
  <img width="1575" height="574" alt="image" src="https://github.com/user-attachments/assets/c95350d3-b5fd-4cb7-b6a5-ef5b74f66c1e" />
</p>

<h4>10. Lorem</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>10a. Lorem</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>10b. Lorem</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>10c. Lorem</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>10d. Lorem</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>10e. Lorem</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>Step 2 Summary</h4>

<p>
Lorem
</p>

<h3>Step 3. Observe SSH Traffic</h3>

<h4>11. Lorem</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>12. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>Step 3 Summary</h4>

<p>
Lorem
</p>
<h3>Step 4. Observe DHCP Traffic</h3>

<h4>13. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>14. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>Step 4 Summary</h4>

<p>
Lorem
</p>

<h3>Step 5. Observe DNS Traffic</h3>

<h4>15. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>16. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>Step 5 Summary</h4>

<p>
Lorem
</p>

<h3>Step 6. Observe RDP Traffic</h3>

<h4>17. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>18. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>Step 6 Summary</h4>

<p>
Lorem
</p>

<h3>Lab Cleanup</h3>

<h4>19. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>20. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>21. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>Lab Cleanup Summary</h4>

<p>
Lorem
</p>

<h2>Conclusion</h2>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>

<h2>Thank you for checking out my project!</h2>

<p>
If you found it helpful or interesting, subscribe to my YouTube channel and 🔗connect with me on LinkedIn by clicking below:
</p>

[<img align="left" alt="Jeramy | YouTube" width="22px" src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/youtube.svg" />][youtube]
[<img align="left" alt="Jeramy | LinkedIn" width="22px" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" />][linkedin]

<br clear="left"/>

[youtube]: https://youtube.com/@jeramycanals
[linkedin]: https://linkedin.com/in/jeramycanals
