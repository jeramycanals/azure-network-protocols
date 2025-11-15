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

- Microsoft Azure (Resource Group, Virtual Machines, Virtual Network, and Subnet)
- Network Security Groups (NSGs)
- Azure Network Watcher
- Remote Desktop (RDP)
- Wireshark (Protocol Analyzer)
- Various Command-Line Tools
- Linux Terminal (Bash)
- ICMP (Ping)
- Secure Shell (SSH)
- DHCP (Dynamic Host Configuration Protocol)
- DNS (Domain Name System

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 22.04

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

<h4>2. Create Windows 10 VM and select the previously created Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>3. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>4. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>

<h3>Step 2. Observe ICMP Traffic</h3>

<h4>5. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>6. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>7. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>8. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>9. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>10. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>

<h3>Step 3. Observe SSH Traffic</h3>

<h4>11. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<h4>12. Create Resource Group</h4>

<p>
  <img width="740" height="333" alt="image" src="https://github.com/user-attachments/assets/f7d9563a-df9d-4e26-a044-851679b9209d" />

</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
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

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
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

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
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

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
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

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
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
