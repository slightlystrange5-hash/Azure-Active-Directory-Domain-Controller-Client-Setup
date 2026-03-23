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

<img width="719" height="720" alt="Screenshot 2026-03-23 150736" src="https://github.com/user-attachments/assets/bce6bd8a-d1e0-44f1-bc47-942077b5ecaa" />
<img width="1644" height="679" alt="Screenshot 2026-03-23 150807" src="https://github.com/user-attachments/assets/533e8b92-471a-4777-afc7-288625f3b638" />
<img width="850" height="942" alt="Screenshot 2026-03-23 150826" src="https://github.com/user-attachments/assets/4f35b51e-3413-4e74-8063-4178655ea0b2" />
<img width="616" height="947" alt="Screenshot 2026-03-23 150834" src="https://github.com/user-attachments/assets/42f1839d-34b4-4415-af92-bc7e9fa865d0" />

---

### Step 2: Create Virtual Network & Subnet

1. Go to **Virtual Networks**
2. Click **Create**
3. Configure:
   - Name: `ADNetwork`
4. Click **Review + Create**, then **Create**

<img width="675" height="883" alt="Screenshot 2026-03-23 150859" src="https://github.com/user-attachments/assets/9ed6eb1a-cb56-4420-864f-b6eebd0bb770" />
<img width="1465" height="704" alt="Screenshot 2026-03-23 150911" src="https://github.com/user-attachments/assets/05bf89e2-97a6-4044-8123-9914afe90836" />
<img width="864" height="946" alt="Screenshot 2026-03-23 150925" src="https://github.com/user-attachments/assets/9fcc4f81-2d4f-4257-ade7-f19f25addaf3" />
<img width="710" height="945" alt="Screenshot 2026-03-23 150933" src="https://github.com/user-attachments/assets/eaa4178e-1fc8-4eef-a695-039c5709d626" />


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
   
<img width="630" height="786" alt="Screenshot 2026-03-23 151007" src="https://github.com/user-attachments/assets/97eaede1-3882-4cd0-82b3-85f080decb53" />
<img width="1531" height="623" alt="Screenshot 2026-03-23 151014" src="https://github.com/user-attachments/assets/4edce75b-9a61-4117-89a4-a316e9a371b5" />
<img width="459" height="229" alt="Screenshot 2026-03-23 151021" src="https://github.com/user-attachments/assets/a2a241c7-6b43-4d91-868f-e9f4e2c2a71e" />
<img width="915" height="941" alt="Screenshot 2026-03-23 151100" src="https://github.com/user-attachments/assets/56ef43e5-d361-4b76-86a8-0908b2ddc28a" />
<img width="823" height="729" alt="Screenshot 2026-03-23 151134" src="https://github.com/user-attachments/assets/30cd0d52-1ba4-4da6-86af-27a175068e4a" />
<img width="692" height="273" alt="Screenshot 2026-03-23 151146" src="https://github.com/user-attachments/assets/afb1f9aa-516b-43aa-bb57-993364aaa1d8" />



---

### Step 4: Set Static Private IP for DC-1

1. Go to **DC-1 → Networking → Network Interface**
2. Click **IP Configuration**
3. Change:
   - Private IP Assignment: **Static**
4. Save changes

<img width="1918" height="698" alt="Screenshot 2026-03-23 151427" src="https://github.com/user-attachments/assets/d5763d29-b374-4e74-8ced-67ef1418a086" />
<img width="823" height="843" alt="Screenshot 2026-03-23 151507" src="https://github.com/user-attachments/assets/b9d6bb8c-1018-4d53-ba84-2a5cb27acba4" />
<img width="1324" height="616" alt="Screenshot 2026-03-23 151520" src="https://github.com/user-attachments/assets/87b8ae29-9a97-4b14-8374-6434c62796d3" />
<img width="1491" height="838" alt="Screenshot 2026-03-23 151533" src="https://github.com/user-attachments/assets/8bc60f70-d9eb-404e-97ac-adc492bba488" />
<img width="588" height="902" alt="Screenshot 2026-03-23 151559" src="https://github.com/user-attachments/assets/baf39fd9-4c72-45f1-8000-1f14bd2aac85" />


---

### Step 5: Disable Windows Firewall (DC-1)

1. Connect to DC-1 via Remote Desktop (RDP)
2. Open **Run → wf.msc**
3. Turn off firewall for:
   - Domain Profile
   - Private Profile
   - Public Profile

> ⚠️ Note: This is for lab/testing purposes only.

<img width="1893" height="461" alt="Screenshot 2026-03-23 151645" src="https://github.com/user-attachments/assets/539e3d6e-f7bb-4de2-af58-f7d7554701c4" />
<img width="1019" height="403" alt="Screenshot 2026-03-23 151707" src="https://github.com/user-attachments/assets/6f6da4d1-0849-4f38-a08c-545cd1d69e79" />
<img width="515" height="443" alt="Screenshot 2026-03-23 151728" src="https://github.com/user-attachments/assets/756ba57d-d6e1-4a3d-8b60-ad28df5e962e" />
<img width="1887" height="1010" alt="Screenshot 2026-03-23 151918" src="https://github.com/user-attachments/assets/faff4397-6a25-4317-a8c2-a289a63ef225" />
<img width="448" height="211" alt="Screenshot 2026-03-23 152057" src="https://github.com/user-attachments/assets/ee0f4e73-3a7c-4b94-a647-3dd873bd8a2e" />
<img width="505" height="683" alt="Screenshot 2026-03-23 152117" src="https://github.com/user-attachments/assets/b41919e4-e724-4ca6-a917-929db7bd9227" />
<img width="399" height="450" alt="Screenshot 2026-03-23 152205" src="https://github.com/user-attachments/assets/9d570589-5871-47e0-b4ca-d7761b8f5cf3" />
<img width="402" height="454" alt="Screenshot 2026-03-23 152216" src="https://github.com/user-attachments/assets/904d9841-89a0-4851-b42e-5695600b864d" />
<img width="397" height="457" alt="Screenshot 2026-03-23 152232" src="https://github.com/user-attachments/assets/efd9e9b6-963a-41c5-be96-49fd8f1e10cb" />


---

### Step 6: Create Client VM (Client-1)

1. Go to **Virtual Machines**
2. Click **Create**
3. Configure:
   - Name: `Client-1`
   - Image: Windows 11
   - Username: `labuser`
   - Password: `Cyberlab123!`
4. Networking:
   - Same **Region**
   - Same **Virtual Network (AD-VNet)**
5. Click **Review + Create**, then **Create**
 - Again, don't forget to check the Licensing box

<img width="625" height="783" alt="Screenshot 2026-03-23 153958" src="https://github.com/user-attachments/assets/2a91b03d-6521-4811-9e2b-f80e4193fa73" />
<img width="1912" height="570" alt="Screenshot 2026-03-23 154007" src="https://github.com/user-attachments/assets/96314029-1609-41d5-b1c5-3de1a025dea3" />
<img width="861" height="870" alt="Screenshot 2026-03-23 154119" src="https://github.com/user-attachments/assets/e4d7d324-43c8-4523-88a9-20f420b823e1" />
<img width="858" height="816" alt="Screenshot 2026-03-23 154149" src="https://github.com/user-attachments/assets/60941404-72fb-4d4b-99be-c25e266ee2f8" />


---

### Step 7: Configure DNS Settings on Client-1

1. Go to **Client-1 → Networking → Network Settings**
2. Click the Hyperlink under Network Interface / IP Configuration
3. Select **DNS Servers**
4. Choose:
   - **Custom DNS**
   - Enter DC-1’s **Private IP Address**
5. Save changes

<img width="1913" height="607" alt="Screenshot 2026-03-23 154611" src="https://github.com/user-attachments/assets/d2ff36de-db1f-4772-b579-ad5733819d5b" />
<img width="1901" height="926" alt="Screenshot 2026-03-23 154932" src="https://github.com/user-attachments/assets/80404f3f-936c-4ec7-8fbd-83cfc2739d15" />
<img width="1330" height="528" alt="Screenshot 2026-03-23 154937" src="https://github.com/user-attachments/assets/11ec78a2-c5cb-471f-a0ef-1dec37d25110" />
<img width="992" height="781" alt="Screenshot 2026-03-23 154946" src="https://github.com/user-attachments/assets/4756e85a-9e9d-42f2-b8e4-fd65de1fa507" />


---

### Step 8: Restart Client-1

1. From Azure Portal:
   - Select **Client-1**
   - Click **Restart**

<img width="1910" height="452" alt="Screenshot 2026-03-23 155143" src="https://github.com/user-attachments/assets/2bbdbc75-3332-49bc-b7c4-f625ad555d35" />
<img width="1874" height="505" alt="Screenshot 2026-03-23 155152" src="https://github.com/user-attachments/assets/0c2efe85-1940-44dd-aa4e-f2e05f27c624" />

---

### Step 9: Test Connectivity (Ping DC-1)

1. Log into **Client-1 via RDP**
2. Open **Command Prompt**
3. Run: ping DC - 1 Private IP Address

4.  Verify successful replies from DC-1

<img width="1892" height="720" alt="Screenshot 2026-03-23 160044" src="https://github.com/user-attachments/assets/40d766cd-fd3e-42b6-a6ab-dfe7be228dd2" />
<img width="968" height="813" alt="Screenshot 2026-03-23 155804" src="https://github.com/user-attachments/assets/1057c363-5c62-48d8-a957-0b81177621fb" />
<img width="1631" height="1011" alt="Screenshot 2026-03-23 155848" src="https://github.com/user-attachments/assets/f474d25b-5e84-4fdb-b12d-3094dd0ef3d0" />
<img width="1215" height="689" alt="Screenshot 2026-03-23 155919" src="https://github.com/user-attachments/assets/2574364e-f91a-4a13-ba41-8742d24f8482" />


---

### Step 10: Verify DNS Configuration

1. On Client-1, open **PowerShell**
2. Run: ipcongig /all
3. Confirm DNS Server shows DC-1 Private IP Address

<img width="967" height="823" alt="Screenshot 2026-03-23 160351" src="https://github.com/user-attachments/assets/53ec7feb-33be-4c6e-bfc4-db785bf462da" />
<img width="1304" height="875" alt="Screenshot 2026-03-23 160416" src="https://github.com/user-attachments/assets/5274416a-3eb1-4a36-baed-8edb5581ae7f" />
<img width="959" height="595" alt="Screenshot 2026-03-23 160441" src="https://github.com/user-attachments/assets/a71bacad-f2b0-48b0-bce0-3d56c6e26341" />
