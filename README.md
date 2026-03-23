# Azure Active Directory Lab: Domain Controller & Client Setup

---

## Project Summary

### Overview
This project is a **hands-on lab and walkthrough** demonstrating how to deploy a basic Active Directory environment in Microsoft Azure. The lab includes configuring a Windows Server as a Domain Controller and connecting a Windows 10 client machine for network communication and DNS validation.

This project simulates a real-world enterprise environment and demonstrates foundational IT and system administration skills.

---

### Languages Used
- PowerShell (for network verification and configuration checks)

---

### Environments Used
- Microsoft Azure (Cloud Platform)
- Windows Server 2022 (Domain Controller)
- Windows 10 (Client Machine)

---

### Technologies / Services Used
- Azure Virtual Machines
- Azure Virtual Network (VNet)
- Azure Resource Groups
- Active Directory (planned for later configuration)
- DNS Configuration

---

## Media

> Replace the placeholders below with your screenshots.

- Resource Group Creation
- Virtual Network Configuration
- Domain Controller VM Setup
- Static IP Configuration
- Firewall Disabled
- Client VM Setup
- DNS Configuration
- Ping Test Results
- PowerShell Output (`ipconfig /all`)

---

## Demonstration

---

### Step 1: Create Resource Group

1. Log into Azure Portal  
2. Navigate to **Resource Groups**  
3. Click **Create**  
4. Configure:
   - Name: `AD-Lab-RG`
   - Region: Same region for all resources  
5. Click **Review + Create**, then **Create**

![Resource Group Screenshot](images/resource-group.png)

---

### Step 2: Create Virtual Network & Subnet

1. Go to **Virtual Networks**
2. Click **Create**
3. Configure:
   - Name: `AD-VNet`
   - Address Space: `10.0.0.0/16`
4. Subnet:
   - Name: `Subnet-1`
   - Address Range: `10.0.1.0/24`
5. Click **Review + Create**, then **Create**

![VNet Screenshot](images/vnet.png)

---

### Step 3: Create Domain Controller VM (DC-1)

1. Navigate to **Virtual Machines**
2. Click **Create → Azure Virtual Machine**
3. Configure:
   - Name: `DC-1`
   - Image: Windows Server 2022
   - Size: Default (or as required)
   - Username: `labuser`
   - Password: `Cyberlab123!`
4. Networking:
   - Attach to `AD-VNet`
   - Subnet: `Subnet-1`
5. Click **Review + Create**, then **Create**

![DC VM Screenshot](images/dc-vm.png)

---

### Step 4: Set Static Private IP for DC-1

1. Go to **DC-1 → Networking → Network Interface**
2. Click **IP Configuration**
3. Change:
   - Private IP Assignment: **Static**
4. Save changes

![Static IP Screenshot](images/static-ip.png)

---

### Step 5: Disable Windows Firewall (DC-1)

1. Connect to DC-1 via Remote Desktop (RDP)
2. Open **Run → wf.msc**
3. Turn off firewall for:
   - Domain Profile
   - Private Profile
   - Public Profile

> ⚠️ Note: This is for lab/testing purposes only.

![Firewall Screenshot](images/firewall.png)

---

### Step 6: Create Client VM (Client-1)

1. Go to **Virtual Machines**
2. Click **Create**
3. Configure:
   - Name: `Client-1`
   - Image: Windows 10
   - Username: `labuser`
   - Password: `Cyberlab123!`
4. Networking:
   - Same **Region**
   - Same **Virtual Network (AD-VNet)**
5. Click **Review + Create**, then **Create**

![Client VM Screenshot](images/client-vm.png)

---

### Step 7: Configure DNS Settings on Client-1

1. Go to **Client-1 → Networking → Network Interface**
2. Select **DNS Settings**
3. Choose:
   - **Custom DNS**
   - Enter DC-1’s **Private IP Address**
4. Save changes

![DNS Screenshot](images/dns.png)

---

### Step 8: Restart Client-1

1. From Azure Portal:
   - Select **Client-1**
   - Click **Restart**

![Restart Screenshot](images/restart.png)

---

### Step 9: Test Connectivity (Ping DC-1)

1. Log into **Client-1 via RDP**
2. Open **Command Prompt**
3. Run:
