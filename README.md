<p align="center">
  <img src="https://github.com/user-attachments/assets/b16601e3-75cc-4e5c-9e85-f95de8baf8eb" alt="![image]"
    </p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual MAchines</h1>
In this tutorial, We will be operating on Microsoft Azure and observing various network traffic to and... <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, HTTPS/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Sysyems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 22.04

<h2>High-Level Steps </h2>

- Creating Resource Groups and Virtual Machines in Azure

<h2>Actions and Observations</h2>

1. Creating Resource Groups and Virtual Machines

 Resource Group:
- To create a Resource Group, go to the Azure Portal. In the middle of the homepage under 'Azure Services', click on 'Resource groups' and then select 'Create' to begin the process'
![Screenshot 2025-05-02 161517](https://github.com/user-attachments/assets/b71ae5ea-cbf2-43b0-8f7d-69a8376dbcff)

- All rescources in a subsciption are billed together so leave that as default.
- Resource group name can be named to your desire. I will call mine "RG-NSGs-Lab".
- When selecting a resource group region, it's recommended that you select a location close to where your control operations originate.
![Screenshot 2025-05-02 2211482](https://github.com/user-attachments/assets/57310bb4-d7c1-4de3-aa04-9f5bded6e110)

- Click 'Review + create'
![Screenshot 2025-05-02 223356](https://github.com/user-attachments/assets/cbeb6f49-381c-4e54-b569-a56d61447b0c)
- Then click 'Create'
![Screenshot 2025-05-02 223508](https://github.com/user-attachments/assets/c13dbdac-728f-496f-ae81-3db33248b357)

 Virtual Machines:
- In the Azure Portal, use the search bar at the top os search for 'Virtual Machines" and select it.
- You are desired to create two virual machines.
- In the display area, click 'Create' then click 'Azure virtual machine'
![Screenshot 2025-05-02 225357](https://github.com/user-attachments/assets/6af18902-841e-4409-8c26-51c1576faed9)
