<p align="center">
  <img width="297" height="65" alt="image" src="https://github.com/user-attachments/assets/499c27ec-8b27-47f7-9f60-c28191276562" />
  <img width="145" height="57" alt="image" src="https://github.com/user-attachments/assets/10050681-339e-406f-906b-0683d42eeb44" />
  <img width="297" height="117" alt="image" src="https://github.com/user-attachments/assets/f3cbff92-dffb-46e0-b8ed-556d7ce170a0" />
</p>

<h1>Network Traffic Analysis Between Azure VMs Using NSGs and Wireshark</h1>

<p> 
This project provides a hands-on lab demonstrating how core network traffic behaves inside a cloud-hosted environment using Microsoft Azure Virtual Machines. The lab walks through creating a Windows 10 VM and an Ubuntu Linux VM inside the same virtual network, installing and using Wireshark to capture traffic, and analyzing how different protocols operate in real time. By using both Windows CMD/PowerShell and Bash on the Ubuntu VM, pinging between VMs (ICMP), connecting over SSH, renewing DHCP leases, performing DNS lookups, and observing continuous RDP traffic, this project illustrates how ICMP, SSH, DHCP, DNS, and RDP packets move across a virtual network and how Network Security Groups (NSGs) affect communication. This lab builds foundational skills in cloud networking, packet analysis, virtual machine connectivity, and network troubleshooting, which are key capabilities for IT support, networking, and cybersecurity professionals. 
</p>

<p align="center">
  <img width="815" height="316" alt="image" src="https://github.com/user-attachments/assets/cc38f654-5332-490f-bd8d-7a7d1cb4d412" />
  <img width="732" height="679" alt="image" src="https://github.com/user-attachments/assets/0848e429-cc27-4225-87d9-2630519094b3" />
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Resource Group, Virtual Network (VNet), Subnet, and Virtual Machines)
- Network Security Groups (NSGs)
- Azure Network Watcher
- Remote Desktop (RDP)
- Wireshark (Protocol Analyzer)
- <img align="center" alt="PowerShell Icon" width="20px" src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/powershell-colored.svg" /> PowerShell Commands: (ping, ipconfig /renew, nslookup, ssh, etc.)
- Linux Terminal (Bash): Commands (id, hostname, uname -a, exit, etc.)
- ICMP (Ping)
- Secure Shell (SSH)
- DHCP (Dynamic Host Configuration Protocol)
- DNS (Domain Name System

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 24.04

<h2>High-Level Steps</h2>

- Step 1. Create Resources
- Step 2. Observe ICMP Traffic in Wireshark
- Step 3. Observe SSH Traffic in Wireshark
- Step 4. Observe DHCP Traffic in Wireshark
- Step 5. Observe DNS Traffic in Wireshark
- Step 6. Observe RDP Traffic in Wireshark

<h3>Step 1. Create Resources</h3>

<h4>1. Create a Resource Group.</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>2. Create a Windows 10 Virtual Machine (VM), and select the previously created Resource Group.</h4>

<p>
  <img width="764" height="701" alt="image" src="https://github.com/user-attachments/assets/df689c31-2a50-401d-a1e2-638e2848ed75" />
  <img width="778" height="712" alt="image" src="https://github.com/user-attachments/assets/ab5412c6-25c9-49c4-b222-25724f63b2a8" />
  <img width="776" height="702" alt="image" src="https://github.com/user-attachments/assets/9283a744-535b-4bc7-937c-e17fcb573ca9" />
</p>

<h4>2a. While creating the VM, allow it to create a new Virtual Network (VNet) and Subnet.</h4>

<p>
  <img width="771" height="694" alt="image" src="https://github.com/user-attachments/assets/43dd2c17-94c2-4751-9271-9e98241bf059" />
</p>

<h4>3. Create a Linux (Ubuntu) VM.</h4>

<p>
  <img width="769" height="697" alt="image" src="https://github.com/user-attachments/assets/8ad69c3d-bd11-404a-b424-89ba20472346" />
  <img width="762" height="637" alt="image" src="https://github.com/user-attachments/assets/128efa86-4f97-41ad-8179-21e3791cc0b7" />
  <img width="770" height="629" alt="image" src="https://github.com/user-attachments/assets/aa0ffa7b-acb8-49cf-8c04-718374e980da" />
</p>

<h4>3a. While creating the VM, select the previously created Resource Group, VNet, and Subnet.</h4>

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

<h3>Step 2. Observe ICMP Traffic in Wireshark</h3>

<h4>5. Use Remote Desktop to connect to your Windows 10 Virtual Machine.</h4>

<p>
  <img width="619" height="377" alt="image" src="https://github.com/user-attachments/assets/0c2b0759-3342-4349-9023-89716d1eff88" />
</p>

<h4>6. Within your Windows 10 Virtual Machine, install Wireshark.</h4>

<p>
  <img width="792" height="586" alt="image" src="https://github.com/user-attachments/assets/4a608f3a-abe2-4f45-bda0-fd6dabcff3cd" />
</p>

<h4>7. Open Wireshark, click "Ethernet", then click the blue shark fin icon to start capturing packets, apply a filter for ICMP traffic only.</h4>

<p>
  <img width="743" height="575" alt="image" src="https://github.com/user-attachments/assets/64914628-4462-4553-9528-55e0d28443ca" />
  <img width="743" height="576" alt="image" src="https://github.com/user-attachments/assets/97b127c6-a9fc-4683-a09c-216673a36af1" />
</p>

<h4>8. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM.</h4>

<p>
  <img width="1269" height="395" alt="image" src="https://github.com/user-attachments/assets/de61a064-aa2a-4a37-b9cf-2a79672df534" />
  <img width="851" height="699" alt="image" src="https://github.com/user-attachments/assets/e143cfb5-877f-4229-b5b9-9670bea1d674" />
</p>

<h4>8a. Observe ping requests and replies within Wireshark.</h4>

<p>
  <img width="773" height="698" alt="image" src="https://github.com/user-attachments/assets/9ac5afd0-839e-4279-b1a9-236bd7e6e50e" />
</p>

<h4>9. From the Windows 10 VM, open PowerShell or Command Prompt, ping a public website (such as www.google.com), and observe the traffic in Wireshark.</h4>

<p>
  <img width="1575" height="574" alt="image" src="https://github.com/user-attachments/assets/c95350d3-b5fd-4cb7-b6a5-ef5b74f66c1e" />
</p>

<h4>10. Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM.</h4>

<p>
  <img width="1622" height="858" alt="image" src="https://github.com/user-attachments/assets/504a1a9b-59e3-452e-b037-150cdad728ef" />
</p>

<h4>10a. Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic by going to linux-vm > Network settings > Network security group: linux-vm-nsg > Settings > Inbound security rules > Add. Use the settings below.</h4>

<p>
  <img width="1902" height="857" alt="image" src="https://github.com/user-attachments/assets/59ebbfec-5d6f-4047-860c-f09a0f7e31e3" />
  <img width="1900" height="454" alt="image" src="https://github.com/user-attachments/assets/ccb8ac35-25e3-4d11-9d0a-209ad7a5d127" />
</p>

<h4>10b. Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the command-line ping activity. With the Linux VM's NSG Inbound security rule blocking ICMP, the ping now shows "Request timed out." In Wireshark, you will see ICMP requests being sent but no replies returning from the Ubuntu Linux VM.</h4>

<p>
  <img width="1716" height="682" alt="image" src="https://github.com/user-attachments/assets/6ebee156-4665-4983-9556-18a947948318" />
</p>

<h4>10c. Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using by deleting the inbound security rule you created.</h4>

<p>
  <img width="1909" height="417" alt="image" src="https://github.com/user-attachments/assets/60895a72-9f61-4414-8e89-627ed85b3b2b" />
</p>

<h4>10d. Back in the Windows 10 VM, observe the ICMP traffic in Wireshark and the command-line ping activity, which should now start working again.</h4>

<p>
  <img width="1760" height="679" alt="image" src="https://github.com/user-attachments/assets/199c553b-2815-4964-ad5c-adbb6e04efd3" />
</p>

<h4>10e. Stop the ping activity by pressing Ctrl+C in the command line and clicking the stop icon in Wireshark.</h4>

<p>
  <img width="1756" height="676" alt="image" src="https://github.com/user-attachments/assets/937b95fd-0d27-4712-9a88-1149f1f4533d" />
</p>

<h4>Step 2 Summary</h4>

<p>
In Step 2, we connect to our Windows 10 VM using Remote Desktop, install Wireshark, and begin capturing network traffic filtered for ICMP. We retrieve the Ubuntu VM’s private IP address and ping it from the Windows VM to observe the ICMP requests and replies in both the command line and Wireshark. We then ping a public website, such as www.google.com, to view the ICMP activity generated by external communication. Next, we initiate a nonstop ping from the Windows VM to the Ubuntu VM and modify the Ubuntu VM’s Network Security Group by disabling inbound ICMP traffic, causing the pings to time out and removing ICMP replies in Wireshark. After re-enabling ICMP in the NSG, we observe the ping traffic resume successfully in both the terminal and Wireshark, and finally stop the continuous ping.
</p>

<h3>Step 3. Observe SSH Traffic in Wireshark</h3>

<h4>11. In Wireshark, start a new packet capture by clicking the green shark-fin icon and selecting "Continue without Saving," then apply the display filter tcp.port == 22 to display SSH traffic only.</h4>

<p>
  <img width="1192" height="688" alt="image" src="https://github.com/user-attachments/assets/2e193309-1469-4e96-b899-9bafa6eb2910" />
  <img width="1173" height="674" alt="image" src="https://github.com/user-attachments/assets/5079848f-cb22-4182-82bd-efdc43b4b87e" />
</p>

<h4>12. From your Windows 10 VM, open PowerShell and initiate an SSH connection to your Ubuntu VM using its private IP address by typing "ssh labuser@Ubuntu-Private-IP" from Step 2, number 8. Type "yes" when prompted and then enter the Ubuntu VM's password when prompted to complete the SSH login. Once connected, observe the SSH traffic appearing in Wireshark.</h4>

<p>
  <img width="1891" height="681" alt="image" src="https://github.com/user-attachments/assets/e9376f7d-7ea3-4df2-8905-10db8c925d8a" />
  <img width="1852" height="683" alt="image" src="https://github.com/user-attachments/assets/9ec493f5-2ec4-4c8b-8459-27b82f097ac0" />
</p>

<h4>12a. Type commands (id, hostname, uname -a, etc) into the Linux SSH connection and observe the SSH traffic spam in Wireshark.</h4>

<p>
  <img width="1852" height="531" alt="image" src="https://github.com/user-attachments/assets/ca49277b-70fe-46aa-9423-51a81c778aa7" />
</p>

<h4>12b. Exit the SSH connection by typing "exit" and pressing [Enter].</h4>

<p>
  <img width="1852" height="531" alt="image" src="https://github.com/user-attachments/assets/29134e64-87d9-4eb1-9af0-97dec9081da0" />
</p>

<h4>Step 3 Summary</h4>

<p>
In Step 3, we analyzed how SSH traffic behaved between two Azure virtual machines. After switching Wireshark to a capture filtered for SSH packets only (tcp.port == 22), we initiated an SSH connection from the Windows 10 VM to the Ubuntu VM using its private IP address. Once logged in, we executed several Linux commands such as id, hostname, and uname -a, which generated encrypted SSH activity and observed the resulting packet flow in Wireshark. Each command produced a burst of encrypted SSH packets, demonstrating how all session data was securely transmitted over the SSH protocol. Finally, we closed the session by typing exit, which ended the SSH connection.
</p>
<h3>Step 4. Observe DHCP Traffic in Wireshark</h3>

<h4>13. Back in Wireshark, start a new capture and apply the display filter "dhcp" to view DHCP traffic only.</h4>

<p>
  <img width="1039" height="535" alt="image" src="https://github.com/user-attachments/assets/7d4824ff-c60d-4795-9de4-0100244bacec" />
</p>

<h4>14. From your Windows 10 VM, attempt to issue the VM a new IP address from the command line (ipconfig /renew).</h4>

<p>
  <img width="811" height="529" alt="image" src="https://github.com/user-attachments/assets/30fc91f3-68e3-4166-856c-151563d8e903" />
</p>

<h4>14a. Observe the DHCP traffic that appears in Wireshark as the Windows VM requests and receives a new IP address.</h4>

<p>
  <img width="1042" height="530" alt="image" src="https://github.com/user-attachments/assets/9d59e48d-a745-4962-a769-03668569412c" />

</p>

<h4>Step 4 Summary</h4>

<p>
In Step 4, we observed how DHCP traffic behaves when a Windows VM requests a new IP lease inside an Azure virtual network. After applying a DHCP filter in Wireshark, we ran ipconfig /renew from the Windows 10 VM to force a DHCP renewal. This triggered a DHCP Request packet from the VM to Azure’s internal DHCP server, followed by a DHCP ACK response granting the lease and confirming that the VM could continue using its assigned IPv4 address. These packets appeared immediately in Wireshark, clearly showing the DHCP handshake process in action.
</p>

<h3>Step 5. Observe DNS Traffic in Wireshark</h3>

<h4>15. In Wireshark, start a new capture and apply the display filter "dns" to view DNS traffic only.</h4>

<p>
  <img width="1244" height="617" alt="image" src="https://github.com/user-attachments/assets/6506c771-0e81-4346-afa6-acfaf812952f" />
</p>

<h4>16. From your Windows 10 VM, use the nslookup command in the terminal to see the IP addresses of disney.com and google.com.</h4>

<p>
  <img width="610" height="553" alt="image" src="https://github.com/user-attachments/assets/8e364c87-d7ae-41f3-bb73-b17e052bebdd" />
</p>

<h4>16a. Observe the DNS traffic in Wireshark that appears when the Windows VM looks up the domain names (disney.com and google.com).</h4>

<p>
  <img width="1213" height="700" alt="image" src="https://github.com/user-attachments/assets/e765ca70-5afb-4bbb-b8ec-8bace3160916" />
</p>

<h4>Step 5 Summary</h4>

<p>
In Step 5, we examined how DNS traffic appeared in Wireshark when performing domain lookups from the Windows 10 VM. After filtering Wireshark to display only DNS traffic, we used the nslookup command to look up the IP addresses for disney.com and google.com. Each lookup generated DNS query and response packets, which were immediately visible in Wireshark. These packets showed the Windows VM sending a request to the DNS server and receiving the corresponding IP address information in return, demonstrating how DNS translates domain names into usable network addresses.
</p>

<h3>Step 6. Observe RDP Traffic in Wireshark</h3>

<h4>17. Back in Wireshark, start a new capture and apply the display filter "tcp.port == 3389" to view RDP traffic only. Observe the immediate nonstop stream of traffic. This occurs because the RDP protocol is constantly showing you a live stream from one computer to another; therefore, traffic is always being transmitted.</h4>

<p>
  <img width="1208" height="699" alt="image" src="https://github.com/user-attachments/assets/c87959f0-c5b1-459c-aa40-99a4130244c6" />
</p>

<h4>Step 6 Summary</h4>

<p>
In Step 6, we analyzed how RDP traffic behaves by applying the Wireshark filter tcp.port == 3389 and observing the packet flow while connected to the Windows 10 VM. Unlike ICMP, SSH, DHCP, or DNS, the RDP protocol produced a constant stream of packets, even when no actions were performed on the remote desktop. This continuous traffic occurred because RDP transmits a live stream of the remote session, requiring ongoing updates to display screen changes, mouse movements, and system states. As a result, the Wireshark capture showed nonstop network activity, demonstrating how RDP maintains an active connection to keep the remote desktop responsive and up to date.
</p>

<h3>Lab Cleanup</h3>

<h4>19. Close the Remote Desktop connection by clicking the X in the top-right corner of the RDP window.</h4>

<p>
  <img width="751" height="252" alt="image" src="https://github.com/user-attachments/assets/23908425-8524-49f9-973f-8d97c973aff8" />
</p>

<h4>20. Delete the Resource Group(s) created at the beginning of this lab by navigating to the Resource Groups page in the Azure portal, selecting the appropriate group, clicking “Delete resource group,” checking the “Apply force delete…” option, and entering the Resource Group name to confirm the deletion.</h4>

<p>
  <img width="848" height="881" alt="image" src="https://github.com/user-attachments/assets/4601f212-5626-4ecd-b5c5-9a66c45aa15c" />
  <img width="566" height="871" alt="image" src="https://github.com/user-attachments/assets/89f3ab1d-9f93-4948-90d7-a8316424757c" />
</p>

<h4>21. Verify that the Resource Group was successfully deleted by refreshing the Resource Groups page in the Azure portal and confirming that it no longer appears in the list.</h4>

<p>
  <img width="1154" height="646" alt="image" src="https://github.com/user-attachments/assets/dbef29cf-e44d-4904-bb2a-0d8467ce4d27" />
</p>

<h4>Lab Cleanup Summary</h4>

<p>
At the end of the lab, we closed the Remote Desktop session and deleted the Resource Group that contained all of the Azure resources created during this lab. Removing the Resource Group ensured that every associated component (virtual machines, networks, disks, and IP addresses) was fully deleted to prevent unnecessary Azure charges. Finally, we verified that the Resource Group was successfully deleted, confirming that the environment was cleaned up properly.
</p>

<h2>Conclusion</h2>

<p>
In this lab, we built a complete cloud-based environment in Azure and used it to visualize how core network protocols behave in real time. By deploying Windows and Linux virtual machines into the same virtual network, configuring Network Security Groups, and capturing traffic with Wireshark, we were able to see exactly how ICMP, SSH, DHCP, DNS, and RDP packets move between hosts and how security rules impact that communication. Each step reinforced a different aspect of cloud networking and packet analysis, from understanding basic connectivity and protocol behavior to observing how encrypted sessions and continuous RDP streams show up in network traffic. Together, these exercises strengthened our skills in troubleshooting, cloud networking, and security-focused thinking, providing a strong foundation for more advanced networking and cybersecurity labs in Azure.
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
