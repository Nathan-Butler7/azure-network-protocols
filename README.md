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
- To create a Resource Group, go to the Azure Portal. In the middle of the homepage under 'Azure Services', click on 'Resource groups' and then select 'Create' to begin the process'.
![Screenshot 2025-05-02 161517](https://github.com/user-attachments/assets/b71ae5ea-cbf2-43b0-8f7d-69a8376dbcff)

- All rescources in a subsciption are billed together so leave that as default.
- Resource group name can be named to your desire. I will call mine "RG-NSGs-Lab".
- When selecting a resource group region, it's recommended that you select a location close to where your control operations originate.
![Screenshot 2025-05-02 2211482](https://github.com/user-attachments/assets/57310bb4-d7c1-4de3-aa04-9f5bded6e110)

- Click 'Review + create'.
![Screenshot 2025-05-02 223356](https://github.com/user-attachments/assets/cbeb6f49-381c-4e54-b569-a56d61447b0c)
- Then click 'Create'.
![Screenshot 2025-05-02 223508](https://github.com/user-attachments/assets/c13dbdac-728f-496f-ae81-3db33248b357)

 Virtual Machines:
- In the Azure Portal, use the search bar at the top os search for 'Virtual Machines" and select it.
- You are desired to create two virual machines.
- In the display area, click 'Create' > 'Azure virtual machine'.
![Screenshot 2025-05-02 225357](https://github.com/user-attachments/assets/6af18902-841e-4409-8c26-51c1576faed9)

- Under 'Project details', assign your new resource group you just created (RG-NSGs-Lab).
- Give your Virtual Machine name "windows-vm".
- Select the resource region the same as the Resource groups ((Asia Pacific) Australia East).
![Screenshot 2025-05-03 002830](https://github.com/user-attachments/assets/7a998ae6-1294-44f3-8505-ec2ea37b34e0)

- For Image, select 'Windows 10 Pro version 22H2 - x64 Gen2'.
- Recommended for 'Size' you utilise "Standard_D2s_v5 - 2 vcpus, 8 GiB memory".
- For 'Administrator Account' create your Username "labuser" and password can be anything. e.g; "Cyberlab123!".
![Screenshot 2025-05-03 004155](https://github.com/user-attachments/assets/fec762f8-fe8c-4778-bbaa-0e5362ef3f47)

- Be sure to tick the box for eligibily of a windows liscence.
- Click 'Next : Disks' > 'Next : Networking'.

![image](https://github.com/user-attachments/assets/abf9bcbe-64bf-4902-a8a7-bacf3eaa65b1)

- Change the 'Virtual Network' name. Click on 'Create new'.
- Change it to "Lab2-Vnet" the click 'ok'.
![image](https://github.com/user-attachments/assets/63a21391-5646-4f3d-bccd-48ca4bdc3b8d)

- Click 'Review + Create'.
![image](https://github.com/user-attachments/assets/7a82ac39-8f99-4fe9-bc17-03c854742699)

- Wait for the VM to process till you see "Validation passed" on the top of the page.
![Screenshot 2025-05-06 141709](https://github.com/user-attachments/assets/0bd90452-ceca-46f3-b2e3-6e792e9a564c)

- Then click 'Create'.
![Screenshot 2025-05-06 141743](https://github.com/user-attachments/assets/86ed7e8f-ccb0-423f-b337-969517eaebf1)

- You have successfully created a Windows Virtual Machine.
- Click on 'Create another VM' for Linux (Ubuntu) VM.
![image](https://github.com/user-attachments/assets/c3b0a520-5df7-4c29-a246-0c5643b25da4)

- Under 'Project details', assign your new resource group you just created (RG-NSGs-Lab).
- Give your Virtual Machine name "linux-vm".
![image](https://github.com/user-attachments/assets/6666c8b8-0b5a-450a-a01b-3a0751da96ef)

- For Image, select 'Ubuntu Server 22.04 LTS - x64 Gen2'.
- Recommended for 'Size' you utilise "Standard_D2s_v5 - 2 vcpus, 8 GiB memory".
![image](https://github.com/user-attachments/assets/7e9e4fb0-7bc3-44b7-9387-82df0beb6e48)

- Under Administrator account for 'Authentication type' click 'Password'.
- Create your Username "labuser" and password can be anything. e.g; "Cyberlab123!".
![image](https://github.com/user-attachments/assets/26f80cdc-5501-45fb-906f-64594df1ec01)

- Click 'Next : Disks' > 'Next : Networking'.
![image](https://github.com/user-attachments/assets/ef7296c4-e998-4e9a-861c-c9da3e8d8a1d)

- Make sure the 'Virtual Network' is "Lab2-Vnet"
![image](https://github.com/user-attachments/assets/9bc6bcbc-21aa-4b95-89a5-3ce66ca6febc)

- Click 'Review + Create'.
![Screenshot 2025-05-03 010234](https://github.com/user-attachments/assets/afac077b-29c2-4129-9728-df473bd7ab1e)

- Wait for the VM to process till you see "Validation passed" on the top of the page.
![Screenshot 2025-05-06 141709](https://github.com/user-attachments/assets/d2a07be8-792c-4d0e-8065-400808893c07)

- Then click 'Create'.
![Screenshot 2025-05-06 141743](https://github.com/user-attachments/assets/f4d082cc-d5a0-4180-8efe-746d9dc2177f)

- You have successfully created a Linux Virtual Machine.
- Search up "Virtual Machines" and click on it, you will see both Virtual Machines.
![image](https://github.com/user-attachments/assets/8b17d796-e31e-4570-8886-6c40d2216545)
