# 📘 Configuring DNS and DHCP on Windows Server for Domain Joined Clients.

## 📍 Project Overview
This project demonstrates the installation and configuration of DHCP and DNS services on a Windows Server 2025 Domain Controller. It includes the creation of a DHCP scope, setting up a forward lookup zone in DNS, and verifying name resolution on client machines.

---

## 📑 Project Objectives
- Set up and configure DNS and DHCP services on an existing Windows Server 2025 Domain Controller 
- Define DHCP scopes and DNS forward lookup zones
- Join Windows 10 and 11 client machines to the domain
- Validate successful network communication via hostname resolution (ping)

---

## 🛠️ Tools & Technologies Used

- 💻 VirtualBox (for virtualization)
- 🖥️ Windows Server 2025
- 🖥️ Windows 10 & 11 (clients)
- ⚙️ Active Directory Domain Services (AD DS)
- 📡 DNS & DHCP Server Roles
- 🧰 Server Manager (GUI-based configuration)
- 🧪 Command-line tools: `ping`, `ipconfig`, `nslookup`

---

## 🛠️ DHCP Server Configuration

### ✅ Step 1: Install the DHCP Role
1. Open **Server Manager** → Click **Add Roles and Features**.

<img width="1136" alt="01-Add roles and features" src="https://github.com/user-attachments/assets/c155f4fe-0e79-4e50-b87a-fa082d429523" />



<img width="981" alt="02 - Wizard" src="https://github.com/user-attachments/assets/5bf517e1-988f-4f7f-b7d1-d8aeba08dd90" />


2. Select **Destination Server**.

<img width="996" alt="03-Select Destination Server" src="https://github.com/user-attachments/assets/37740bdf-c3b0-4462-8fa7-864d99c841d0" />


3. Select your server and check **DHCP Server**.

<img width="990" alt="04-Select Server Roles " src="https://github.com/user-attachments/assets/72f881f6-da8b-46f0-ba15-1bfaadd97c42" />



<img width="518" alt="05- Add Features" src="https://github.com/user-attachments/assets/9a4c6a4c-1772-4ed3-9119-83f50e1eeb00" />


4. Click **Install** → **Close**  after installation. 

<img width="980" alt="06-Confirm Installations" src="https://github.com/user-attachments/assets/5c757374-d798-43d1-9068-0e3b9b31436f" />


<img width="983" alt="07- Installation in Progress" src="https://github.com/user-attachments/assets/d584e953-e421-4d82-9546-dc335dbd7f48" />

5. **Complete DHCP Post-Install Configuration** 

<img width="419" alt="08-Post-Deployment Config" src="https://github.com/user-attachments/assets/2b41d929-11ce-41a8-b9e6-247643201138" />


<img width="944" alt="09-Admin-and-User-Group" src="https://github.com/user-attachments/assets/4ccda1f5-9906-4dcf-9f08-b2c2c26440a6" />


<img width="950" alt="10-Authorization" src="https://github.com/user-attachments/assets/7e9485e2-6c7e-4f72-a109-5cfdfcc38ec0" />


<img width="956" alt="11-Done" src="https://github.com/user-attachments/assets/77ff9dec-75eb-4c0b-a6c8-5280197fd74f" />


<img width="1124" alt="12-DHCP-Added" src="https://github.com/user-attachments/assets/0847d599-c0d2-47a9-ae24-ed5f6dabc3dd" />

---

### ✅ Step 2: Create and Configure a DHCP Scope
1. Open **DHCP Management Console**.

<img width="1252" alt="13-Create -Scope" src="https://github.com/user-attachments/assets/c93210a9-f01a-4beb-af06-f47bd3503425" />


<img width="829" alt="14-DHCP - Authorized" src="https://github.com/user-attachments/assets/2cdfdb08-41bf-46a1-bef7-980418b5c2cd" />


2. Right-click **IPv4** → Select **New Scope**.

<img width="1021" alt="15-Add a new Scope" src="https://github.com/user-attachments/assets/de2d81f3-e8d2-4432-bd05-a2377d710e1d" />


3. Name your scope (*LocalNetwork*).

<img width="647" alt="15-Name DHCP" src="https://github.com/user-attachments/assets/235b9732-6bd2-4286-b6c0-59b5e806ba55" />


4. Define:
   - **Start IP**: 10.10.10.50
   - **End IP**: 10.10.10.150
   - **Subnet Mask**: 255.255.255.0
   - **DNS Server**: Domain Controller IP (e.g., 10.10.10.10)

<img width="646" alt="16-Define-Address Range" src="https://github.com/user-attachments/assets/ab3fed9c-b8ab-4536-a74b-481b6bfb1494" />

5. **Add Exluded Addresses & Lease period**

<img width="650" alt="17-Add-Exclusion" src="https://github.com/user-attachments/assets/484cdaeb-6678-45e2-b239-c158dba80913" />


<img width="646" alt="18-Lease-days" src="https://github.com/user-attachments/assets/0d3556dd-081c-4580-818d-24e2180e571b" />


<img width="646" alt="19-Scope Finished" src="https://github.com/user-attachments/assets/5f995955-a820-49cf-9d99-48f01b3490db" />

---

### ✅ Step 3: Activate the Scope
**1. In the DHCP Console → Right-click on your newly created scope →** *Activate*.

<img width="1037" alt="21-Activate Scope" src="https://github.com/user-attachments/assets/57936b65-f23d-4125-80b1-408238ebfad6" />


<img width="1009" alt="22-Scope Activated" src="https://github.com/user-attachments/assets/adebcd75-df13-4b01-8f8b-b5c34fb2147a" />


**2. Verify the Activated Scope**

<img width="1041" alt="20- Scope Installed" src="https://github.com/user-attachments/assets/aea1ccc7-5994-4970-8e40-943d388fe3da" />

---

### 🔍 Step 4: Verify DHCP on Clients
1. Boot the Windows 10 or 11 VM.
2. Open **Command Prompt** and run:

<img width="1051" alt="24-TestDHCPWin10" src="https://github.com/user-attachments/assets/1925c46d-e4ca-48d6-856f-568683e3e33c" />


<img width="826" alt="23-TestDHCPWin11" src="https://github.com/user-attachments/assets/d8c7f66f-c37c-4271-87bd-16a9e26ec0bf" />



## 🌐 DNS Forward Lookup Zone Configuration


### ✅ Step 1: Create a Forward Lookup Zone
Open DNS Manager.

<img width="1102" alt="01-Start DNS Config" src="https://github.com/user-attachments/assets/38da266b-f43a-4e30-ab1e-9f728133325a" />

**Expand the server node → Right-click Forward Lookup Zones → New Zone.**

<img width="948" alt="02-NewForwardLookUpZon" src="https://github.com/user-attachments/assets/cbfd74b2-e75c-4659-9353-7789673d7208" />


<img width="821" alt="03-NewZoneWizard" src="https://github.com/user-attachments/assets/967cd840-8a25-4eca-a3c4-42ae27213f2f" />


**Choose Primary Zone → Name it* **seun.local**

<img width="612" alt="04-PryZoneType" src="https://github.com/user-attachments/assets/9d4fcfbe-2cc7-4233-99f8-d30dfe46c563" />


<img width="619" alt="05-ReplicatioWizard" src="https://github.com/user-attachments/assets/1677c7f6-93b6-4b76-ab8c-fb3f02ba161c" />


<img width="617" alt="06-ZoneName" src="https://github.com/user-attachments/assets/aec05a81-e5dc-49ec-97ff-d36c01b9cf82" />


*Allow dynamic updates (secure/non-secure if domain-joined).*

<img width="623" alt="07-DynamicUpdate" src="https://github.com/user-attachments/assets/3d0b70e8-e08e-49ca-bfb6-f84f4d9de69c" />


<img width="623" alt="08-CompleteWizard" src="https://github.com/user-attachments/assets/44231fa7-e5c0-4269-a5b6-8f783fa4b8e0" />

*Verify Zone Addition*

<img width="940" alt="09-NewZoneAdded" src="https://github.com/user-attachments/assets/7987a206-3ef1-4812-946a-5e910c0022a5" />


### 🔍 Step 2: Verify DNS from Clients
**On a Windows 10 client:**

<img width="692" alt="11-ConnectWin11toDomain" src="https://github.com/user-attachments/assets/11946d38-14ab-4261-9bd9-0836b9064425" />

![12-WelcomeWin11toDomain](https://github.com/user-attachments/assets/5fc3e754-a0a5-4eb8-a2b7-f9348b4609ad)


**On a Windows 11 client:**

<img width="715" alt="13-ConnectWin10toDomain" src="https://github.com/user-attachments/assets/18d05a51-2d62-40ef-89ec-b550ac6afa2a" />

![14-RestartSystems](https://github.com/user-attachments/assets/59648cd2-3e59-4308-bebe-7157a2348b2e)

**Confirm Windows Clients Addition to the DNS Zone**

<img width="800" alt="15-DNSJoinAutomatically" src="https://github.com/user-attachments/assets/60b5e044-c48f-4b98-9e97-94cb6f9a044b" />


## ✅ Test hostname resolution:

**Ping server (DC-01) from Windows 10 Client.**
<img width="924" alt="16-ConnectUsingNames" src="https://github.com/user-attachments/assets/1ae81542-1284-4ea3-a446-683b0dbcbf23" />

<img width="824" alt="19-Win10withDNS" src="https://github.com/user-attachments/assets/6623eda9-faaf-4ad8-bb88-6b06eef00b4f" />

**Ping server (DC-01) from Windows 11 Client.**

<img width="873" alt="17-ConnectUsingNames" src="https://github.com/user-attachments/assets/7ac63118-55e5-4b7c-98cc-5f8b2d8bffdf" />


<img width="1139" alt="18-DomainNameEstablished" src="https://github.com/user-attachments/assets/601d70f2-0eab-48f0-b09b-1a6d23bd1cd4" />

## 🧠 Skills Demonstrated

- Windows Server role installation and GUI-based configuration
- Active Directory deployment and domain promotion
- DHCP scope planning and configuration
- DNS zone creation and hostname resolution
- Client-server network troubleshooting
- Basic networking (static vs dynamic IPs, ping, nslookup)


## © License

This lab project is for educational and portfolio purposes only.


