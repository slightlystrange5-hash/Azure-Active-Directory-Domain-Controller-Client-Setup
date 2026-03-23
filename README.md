<img width="608" height="384" alt="AD PHOTO" src="https://github.com/user-attachments/assets/502b4431-e80d-48d4-a811-0dff6c499b3a" />

# Azure Active Directory: Domain Controller & Client Setup

---

## Project Summary

### Overview
This project is a **hands-on walkthrough** demonstrating how to deploy a basic Active Directory environment in Microsoft Azure. The walkthrough includes configuring a Windows Server as a Domain Controller and connecting a Windows 10 client machine for network communication and DNS validation.

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
   - Name: `ADResource`
   - Region: Same region for all resources  
5. Click **Review + Create**, then **Create**

<img width="1915" height="947" alt="Screenshot 2026-03-22 145320" src="https://github.com/user-attachments/assets/c5da7eb9-5cea-4a36-8f56-3f3bc8e66ce5" />

<img width="810" height="658" alt="Screenshot 2026-03-22 145357" src="https://github.com/user-attachments/assets/8f25c44d-59f1-459a-add4-41dd168c1b7c" />

---

### Step 2: Create Virtual Network & Subnet

1. Go to **Virtual Networks**
2. Click **Create**
3. Configure:
   - Name: `ADNetwork`
4. Click **Review + Create**, then **Create**

<img width="1433" height="830" alt="Screenshot 2026-03-22 145427" src="https://github.com/user-attachments/assets/b21f613b-5fc9-4a67-a87d-80798fe32ec9" />

<img width="894" height="838" alt="Screenshot 2026-03-22 145444" src="https://github.com/user-attachments/assets/a282d28b-7e51-4ac9-a885-e407fbb7bf5c" />

---

### Step 3: Create Domain Controller VM (DC-1)

1. Navigate to **Virtual Machines**
2. Click **Create → Azure Virtual Machine**
3. Configure:
   - Name: `Domain Controller`
   - Image: Windows Server 2022
   - Size: Default (or as required)
   - Username: `Labuser`
   - Password: `Cyberlab123!`
4. Networking:
   - Attach to `ADNetwork`
5. Click **Review + Create**, then **Create**
   -Don't forget to check the licesning box
   
<img width="1911" height="946" alt="Screenshot 2026-03-22 145629" src="https://github.com/user-attachments/assets/616bc7c1-9547-4986-8c59-b9b68ba6f85c" />
<img width="912" height="748" alt="Screenshot 2026-03-22 145730" src="https://github.com/user-attachments/assets/fa5d2ac2-b211-4a60-9d36-8aac3bb41121" />
<img width="840" height="811" alt="Screenshot 2026-03-22 145812" src="https://github.com/user-attachments/assets/86be8824-c17b-4770-83b6-96dfafc7a991" />
<img width="584" height="228" alt="Screenshot 2026-03-22 145820" src="https://github.com/user-attachments/assets/c54fd522-9d49-4e65-b4f8-fb83c05ee2e5" />


---

### Step 4: Set Static Private IP for DC-1

1. Go to **DC-1 → Networking → Network Interface**
2. Click **IP Configuration**
3. Change:
   - Private IP Assignment: **Static**
4. Save changes

<img width="1422" height="348" alt="Screenshot 2026-03-22 150004" src="https://github.com/user-attachments/assets/a03f7e23-6e13-48f4-a8a7-d9afaec7346e" />
<img width="292" height="859" alt="Screenshot 2026-03-22 150022" src="https://github.com/user-attachments/assets/642998bf-421d-47bf-bb62-e396a9396fb1" />
<img width="623" height="126" alt="Screenshot 2026-03-22 150030" src="https://github.com/user-attachments/assets/4d354922-b741-4e8b-b651-451b6149cf38" />
<img width="980" height="153" alt="Screenshot 2026-03-22 150037" src="https://github.com/user-attachments/assets/5dbc7e87-348c-4613-9ea7-09c03d103e90" />
<img width="579" height="889" alt="Screenshot 2026-03-22 150048" src="https://github.com/user-attachments/assets/4c24fb83-3504-4b61-94e4-6368c152e344" />


---

### Step 5: Disable Windows Firewall (DC-1)

1. Connect to DC-1 via Remote Desktop (RDP)
2. Open **Run → wf.msc**
3. Turn off firewall for:
   - Domain Profile
   - Private Profile
   - Public Profile

> ⚠️ Note: This is for lab/testing purposes only.
<img width="411" height="250" alt="Screenshot 2026-03-22 150140" src="https://github.com/user-attachments/assets/d236fe29-c883-4eb3-9758-1496973208c4" />
<img width="453" height="398" alt="Screenshot 2026-03-22 150149" src="https://github.com/user-attachments/assets/6ed07f67-ca8e-4d0b-a669-588055acc472" />
<img width="1047" height="787" alt="Screenshot 2026-03-22 150614" src="https://github.com/user-attachments/assets/373923f8-ca8c-4fc7-a60c-619a7064f22e" />
<img width="471" height="49" alt="Screenshot 2026-03-22 150620" src="https://github.com/user-attachments/assets/9bf35a8f-4e23-4666-a62b-81115c8260a0" />
<img width="398" height="451" alt="Screenshot 2026-03-22 150643" src="https://github.com/user-attachments/assets/300bfbfa-4856-4f2b-969b-2dc875f79a69" />
<img width="398" height="454" alt="Screenshot 2026-03-22 150708" src="https://github.com/user-attachments/assets/faa05354-a68d-42a8-9e8b-5f3608891dcd" />
<img width="401" height="455" alt="Screenshot 2026-03-22 150703" src="https://github.com/user-attachments/assets/1123d18f-2190-4441-bb6b-dd4100e4ad04" />

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
3. Run: ping DC - 1 Private IP Address

4.  Verify successful replies from DC-1

![Ping Screenshot](images/ping.png)

---

### Step 10: Verify DNS Configuration

1. On Client-1, open **PowerShell**
2. Run: ipcongig /all
3. Confirm DNS Server shows DC-1 Private IP Address
