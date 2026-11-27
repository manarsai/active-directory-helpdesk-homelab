# 01 - Initial Lab Setup

## Overview

This document records the initial setup of my Active Directory and Helpdesk Home Lab for the fictional company Northstar Solutions.

The first stage involved installing VirtualBox, creating a Windows Server virtual machine and configuring its network settings.

## Step 1 - Install Oracle VirtualBox

I installed Oracle VirtualBox on my Windows 11 laptop.

**Purpose:**

VirtualBox is virtualisation software that allows me to run additional computers inside my physical computer.

I will use it to create a virtual server and virtual employee workstations without needing separate physical machines.

## Step 2 - Create the DC01 Virtual Machine

I created a virtual machine named `DC01` in VirtualBox.

I configured it with:

- Operating system: Windows Server 2025
- RAM: 4 GB
- Processors: 2
- Virtual hard disk: 70 GB
- Storage: Dynamically allocated

**Purpose:**

DC01 will act as the central server for the fictional company's network.

The employee workstations will eventually connect to this server.

<img width="1072" height="706" alt="image" src="https://github.com/user-attachments/assets/f31d1ce7-841b-4ca8-b131-cce8e7524fd8" />


## Step 3 - Install Windows Server 2025

I installed Windows Server 2025 Standard Evaluation with Desktop Experience on DC01.

I also configured the Administrator password.

**Purpose:**

Windows Server is the operating system that will run the company's central IT services, including Active Directory and DNS.

Desktop Experience provides a graphical interface, making it easier to manage the server while learning.

## Step 4 - Rename the Server

I renamed the virtual server to `DC01` and restarted it.

**Purpose:**

Using a clear server name makes it easier to identify and manage computers within a network.

DC01 stands for Domain Controller 01, which is the role I intend this server to perform.

<img width="1076" height="523" alt="image" src="https://github.com/user-attachments/assets/700bf90a-0804-41c4-9414-5cbdcafd076c" />


## Step 5 - Configure Virtual Network Adapters

I configured two network adapters in VirtualBox.

**Adapter 1 - NAT**

- Provides the virtual server with internet connectivity.
- Allows the server to access the internet through my physical laptop's connection.

**Adapter 2 - Internal Network**

- Connected to an internal VirtualBox network named `NORTHSTAR`.
- Provides a private network for communication between the server and future employee workstations.

**Purpose:**

Separating internet connectivity from the private lab network allows me to simulate a small company network without connecting the lab computers directly to my home network.

## Step 6 - Configure a Static IP Address

I configured the internal network adapter on DC01 with the following static IP settings:

| Setting | Value |
|---|---|
| IP Address | 192.168.10.10 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | Blank |
| Preferred DNS | 192.168.10.10 |

**Purpose:**

A static IP address ensures the server keeps the same address on the private network.

This is important because future client computers need to reliably locate the server.

The internal adapter does not have a default gateway because the NAT adapter provides the server's internet connectivity.

## Step 7 - Install Active Directory Domain Services

I used Server Manager to install the Active Directory Domain Services (AD DS) role.

The installation completed successfully.

**Purpose:**

Active Directory Domain Services is the Windows Server role that allows a server to manage users, computers and other network resources centrally.

This is an essential part of the lab because I will use it to simulate employee account management and common helpdesk tasks.

**Important:** Installing the AD DS role does not automatically make the server a Domain Controller. The server still needs to be promoted and configured.

## Current Lab Configuration

| Component | Configuration |
|---|---|
| Server Name | DC01 |
| Operating System | Windows Server 2025 Standard Evaluation |
| Virtualisation | Oracle VirtualBox |
| NAT IP Address | 10.0.2.15 |
| Internal Network | NORTHSTAR |
| Internal IP Address | 192.168.10.10 |
| AD DS Role | Installed |
| Domain | Not yet created |
| Domain Controller | Not yet promoted |

## Next Steps

- Promote DC01 to a Domain Controller.
- Create the `northstar.local` domain.
- Configure and verify DNS.
- Create employee accounts and security groups.
- Set up a Windows 11 client workstation.
- Join the workstation to the domain.

## Skills Practised So Far

- Virtualisation using Oracle VirtualBox.
- Installing Windows Server 2025.
- Basic server configuration.
- Understanding NAT and Internal Network adapters.
- Static IP addressing.
- Installing Windows Server roles and features.
- Understanding the purpose of Active Directory.
