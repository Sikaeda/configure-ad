<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create a Resource Group
- Create a Virtual Network
- Create a Virtual Machine to simulate Domain Controller
- Create a Virtual Machine to simulate a client

<h2>Deployment and Configuration Steps</h2>

![image](https://github.com/user-attachments/assets/5f16150a-bfaa-4daa-bb99-7f03ee8b737c)
![image](https://github.com/user-attachments/assets/220f85e9-ded3-46ee-986b-30e5abb4c7b5)


<p>
Create a resource group. A Resource Group in Microsoft Azure is like a folder where you organize and manage related resources (like virtual machines, databases, storage, and networks). It helps keep everything grouped together so you can easily manage, monitor, and apply settings like security and permissions to all the resources inside it.
</p>
<br />

![image](https://github.com/user-attachments/assets/85199c19-d059-4f7b-8bfd-8286ef7b42eb)
![image](https://github.com/user-attachments/assets/0a988841-6c7c-4393-9298-ac16e9f88d14)

<p>
Create a virtual network. A Virtual Network (VNet) in Microsoft Azure is like a private network in the cloud. It allows different resources (like virtual machines, databases, and apps) to securely communicate with each other, just like devices on a physical network in an office or data center. It also lets you connect to on-premises networks if needed.
</p>
<br />

![image](https://github.com/user-attachments/assets/66166434-83f7-489f-8512-92cd81bcf8f8)
![image](https://github.com/user-attachments/assets/e89a2b73-55d6-4bc2-be83-5c8cee5e14c3)
![image](https://github.com/user-attachments/assets/1d592754-16da-4ee9-ba3f-a62b0464eb96)
![image](https://github.com/user-attachments/assets/cf1d7328-7fc1-4fcf-8cf7-1b4b5770dcc3)
![image](https://github.com/user-attachments/assets/cd8f8163-8107-4f84-8c38-ca052ff242c2)

<p>
Follow the steps in the pictures to create a virtual machine (Don't forget to setup a username and password.) A Virtual Machine (VM) in Microsoft Azure is like a computer in the cloud that you can use to run applications, store data, or host services. It works just like a physical computer but is hosted on Microsoft's servers, allowing you to choose the operating system, processing power, and storage based on your needs.
  After VM is created, set Domain Controller’s NIC Private IP address to be static
  Log into the VM and disable the Windows Firewall (for testing connectivity) using remote desktop and entering the public IP address to connect to the virtual machine. When prompted- select another user and enter the username and password you made. 
  
  ![image](https://github.com/user-attachments/assets/f4410225-6ac9-4e45-b783-9522f099e7cd)

  ![image](https://github.com/user-attachments/assets/c4e318bd-8f8c-43fc-bb3f-5787817da841)
Navigate to the virutual machine "dc-1" Click it. Go to Networking -> Network Settings and click the NIC card at the top of the section.

![image](https://github.com/user-attachments/assets/9125cbba-a242-4f53-acf4-6a30fb0bd341)
Click on ipconfig1 and set the IP to static.

Create the Client VM (Windows 10) named “Client-1”
Setup a username and password
Attach it to the same region and Virtual Network as DC-1

![image](https://github.com/user-attachments/assets/b9730703-52f4-4e90-8ba3-ce6507c55ed0)

After VM is created, set Client-1’s DNS settings to DC-1’s Private IP address
From the Azure Portal, restart Client-1
Login to Client-1 
Attempt to ping DC-1’s private IP address
Ensure the ping succeeded
From Client-1, open PowerShell and run ipconfig /all
The output for the DNS settings should show DC-1’s private IP Address



</p>
<br />
