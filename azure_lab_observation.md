# Azure Networking & Traffic Observation Lab

In this lab, I set up virtual machines in Microsoft Azure, observed different types of network traffic using Wireshark, and experimented with firewall rules. Below is my personal walkthrough and reflections.   

---

## Part 1: Creating Virtual Machines

🔗 [Azure Portal](https://portal.azure.com/)

- Created a **Resource Group** to organize my lab environment.
- Created a **Windows 10 Virtual Machine (VM)** and allowed it to create a **new Virtual Network (VNet)** and **Subnet**.
- Created a **Linux (Ubuntu) VM** in the **same VNet and Subnet** as the Windows VM.
- Used **username/password authentication**.
- Confirmed that both VMs were in the same network so they could communicate.
# Resoure Group
<img width="1920" height="924" alt="creating resource group" src="https://github.com/user-attachments/assets/e79600fb-6bcc-44c4-81a7-eb13101d5075" />
<img width="1917" height="765" alt="resource group created" src="https://github.com/user-attachments/assets/df62de33-8f29-45dd-86f0-4f9034231deb" />

# Windows VM
<img width="1907" height="884" alt="virtual machine" src="https://github.com/user-attachments/assets/32f95030-4258-42fa-936b-552ab0598837" />
<img width="1141" height="724" alt="vm parts1" src="https://github.com/user-attachments/assets/03c5ea5f-d7c8-4ed3-8a97-4d5019635cb0" />
<img width="1920" height="756" alt="vm parts2" src="https://github.com/user-attachments/assets/203c342b-8b8a-41f9-bb44-3a78f486eac8" />
<img width="1030" height="798" alt="vm part3 (Cyberlab123!)" src="https://github.com/user-attachments/assets/e41dfeea-b1c6-48cd-8766-df18ed517f30" />
<img width="1294" height="720" alt="creating the virtual network" src="https://github.com/user-attachments/assets/b2780a2b-7f80-49f4-b0c0-9bed9289ccd5" />
<img width="1233" height="811" alt="editing virtual network" src="https://github.com/user-attachments/assets/bd7ff862-20d2-4a29-92a1-4b392b13eddb" />
<img width="1282" height="842" alt="after creating the virtual network" src="https://github.com/user-attachments/assets/725827dd-9eab-4111-8aaf-98656fdc9cb6" />
<img width="1029" height="877" alt="after creating the virtual machine hit create" src="https://github.com/user-attachments/assets/7e7b7691-792c-4548-aace-a3f16c4afe43" />

## Linux VM
<img width="1492" height="795" alt="linux vm1" src="https://github.com/user-attachments/assets/d2110017-c8e4-4dbc-b2c1-a95ff2f3cd12" />
<img width="1137" height="800" alt="linux vm2" src="https://github.com/user-attachments/assets/a4049339-b857-4c9a-919c-f0133808add9" />
<img width="1306" height="720" alt="vm linux part 3(Cyberlab123!)" src="https://github.com/user-attachments/assets/0828c567-f7b4-4ac9-a6a3-a32246d979ab" />
<img width="1124" height="863" alt="virtual network linux" src="https://github.com/user-attachments/assets/71ec498a-5519-495d-9d5e-923c89678e8f" />

## Virtual Machines
<img width="1578" height="568" alt="virtual machines" src="https://github.com/user-attachments/assets/7460d3df-856e-429c-bceb-311ba31ca9ec" />



















### What I Learned
- How **Resource Groups** act like containers for resources in Azure.
- Why keeping both VMs in the same **VNet/Subnet** is important for internal communication.
- The difference between **Windows VM (for management/observation)** and **Linux VM (for testing traffic)**.

---

## Part 2: Observing ICMP Traffic

- Used **Microsoft Remote Desktop** to connect to my Windows VM.
- Installed **Wireshark** on the Windows VM.
- Started a packet capture and applied a filter for **ICMP traffic**.
- Retrieved the **private IP address** of my Ubuntu VM and pinged it from the Windows VM.
- Observed ICMP **requests and replies** in Wireshark.
<img width="1866" height="961" alt="connecting to windows vm" src="https://github.com/user-attachments/assets/874feb56-465d-4023-9472-0757424b8e92" />
<img width="578" height="607" alt="wvm cred" src="https://github.com/user-attachments/assets/40598c33-918b-4247-bac9-d8fb17d8abaf" />
<img width="1549" height="944" alt="inital config wvm" src="https://github.com/user-attachments/assets/b7fc4b7f-e2e9-4999-ad0b-0fd75cf1039d" />
<img width="1671" height="561" alt="wireshark installation" src="https://github.com/user-attachments/assets/f135391b-be54-4aa0-b1fe-5185ed15e485" />
<img width="786" height="582" alt="wireshark1" src="https://github.com/user-attachments/assets/e9969631-5335-4583-b38f-f96a6708828a" />
<img width="956" height="769" alt="wireshark use" src="https://github.com/user-attachments/assets/661a050f-e29f-438c-8d59-07fed51fd8bd" />
<img width="1721" height="1012" alt="filter for icmp" src="https://github.com/user-attachments/assets/daca4f71-bf9e-49e3-a89c-cb0041bb7513" />
<img width="1883" height="889" alt="get the linux private ip address" src="https://github.com/user-attachments/assets/54599dae-2993-459f-bce9-fe22a7a453b4" />
<img width="1588" height="500" alt="ping the linux virtual machine private ip" src="https://github.com/user-attachments/assets/984919d4-6afa-4609-8fad-57dde095837a" />
<img width="1746" height="574" alt="icmp traffic" src="https://github.com/user-attachments/assets/c7fb3351-af48-42fd-8d98-58e192b899dc" />
<img width="1756" height="907" alt="inspecting packet" src="https://github.com/user-attachments/assets/9b0aadd9-c7fe-4a83-9dc6-529bcece1d8d" />
<img width="982" height="449" alt="inspecting packet2" src="https://github.com/user-attachments/assets/5388c4a2-1b1d-4f99-ae7f-29969e1e0335" />














### What I Learned
- ICMP packets are how devices communicate using **ping**.
- How to filter for ICMP traffic on Wireshark.
- Some parts of the ICMP packet

---

## Part 3: Network Security Group (Firewall) & Traffic Types

### 🔒 Blocking ICMP Traffic
- Started a **continuous ping** from Windows → Ubuntu VM.
- Disabled **inbound ICMP traffic** in the Ubuntu VM’s **Network Security Group (NSG)**.
- Observed in Wireshark that ICMP stopped responding.
- Re-enabled ICMP, and pings started working again.
<img width="1738" height="941" alt="-t" src="https://github.com/user-attachments/assets/b2cbf8d2-a922-4ba9-8555-422546bd0d69" />
<img width="1876" height="617" alt="linux vm networking" src="https://github.com/user-attachments/assets/58535d39-cc00-4f99-a24f-c38a70ec3177" />
<img width="1919" height="831" alt="inbound security rules" src="https://github.com/user-attachments/assets/6b248eb6-ff27-45b2-86b8-0996a6774ee1" />
<img width="1920" height="925" alt="inbound security rules add" src="https://github.com/user-attachments/assets/327e6583-b023-48c3-ac14-61ef55512fd1" />
<img width="734" height="771" alt="inbound security rules add2" src="https://github.com/user-attachments/assets/83f99541-dee4-447c-8d6f-741c838191c6" />
<img width="1916" height="704" alt="rule added icmp" src="https://github.com/user-attachments/assets/daedd26a-501d-4d52-9329-f6e582be9e5b" />
<img width="1459" height="722" alt="affect of the rule" src="https://github.com/user-attachments/assets/fa16484a-a13b-459d-832e-aacd862fca26" />
<img width="1808" height="646" alt="affect of the rule 2" src="https://github.com/user-attachments/assets/3df3015c-19a5-4247-8e5b-3239964a2789" />
<img width="1591" height="451" alt="deleting rule icmp" src="https://github.com/user-attachments/assets/512159b5-604c-4513-a8ec-f005d4e38f91" />
<img width="1835" height="1005" alt="affect of deleting the rule" src="https://github.com/user-attachments/assets/cc524e3e-9aa6-4942-9bfd-71b940ebbb10" />
<img width="1006" height="418" alt="stop the ping" src="https://github.com/user-attachments/assets/bd949fc5-17fd-4060-8b26-7976ae3830e5" />














#### What I Learned
- How **firewall rules** directly affect traffic.
- ICMP is very useful for testing connectivity, but it can also be controlled for security.

---

### 🔑 Observing SSH Traffic
- In Wireshark, applied a filter for **SSH traffic**.
- From Windows, ran:
  ```powershell
  ssh labuser@<Ubuntu Private IP>
  ```
- Logged into Ubuntu and ran basic commands.
- Observed **encrypted SSH packets** in Wireshark.



#### What I Learned
- SSH encrypts communication (you can’t read commands in Wireshark, just see encrypted packets).
- Why SSH is much more secure than plain text protocols.

---

### 🟢 Observing DHCP Traffic
- In Wireshark, filtered for **DHCP**.
- On Windows VM, renewed IP with:
  ```powershell
  ipconfig /renew
  ```
- Observed DHCP negotiation process.



#### What I Learned
- DHCP assigns IPs dynamically.
- You can watch the whole **DISCOVER → OFFER → REQUEST → ACK** handshake in real-time.

---

### 🌐 Observing DNS Traffic
- In Wireshark, filtered for **DNS**.
- Ran:
  ```powershell
  nslookup disney.com
  nslookup pixar.com
  ```
- Observed DNS queries and responses.
<img width="1911" height="1031" alt="results dns" src="https://github.com/user-attachments/assets/513ac325-62b7-4a66-91c2-64f8956fbd0c" />
<img width="1874" height="1012" alt="dns results" src="https://github.com/user-attachments/assets/328dc46d-5b21-4496-8d20-cf4d84982424" />




#### What I Learned
- DNS resolves domain names into IPs.
- Each lookup creates visible DNS query/response traffic.

---

### 🖥️ Observing RDP Traffic
- In Wireshark, filtered for:
  ```
  tcp.port == 3389
  ```
- Saw **constant RDP traffic spam** while connected via Remote Desktop.
<img width="1918" height="1009" alt="rdp traffic" src="https://github.com/user-attachments/assets/2af06693-eb1a-44ca-8ad5-e62ae5c18b5a" />


#### What I Learned
- RDP constantly streams desktop updates, so it generates **non-stop traffic**.
- It’s not just when you type or click everything is live-streamed.

---

## 🔥 Lab Cleanup
- Closed Remote Desktop connection.
- Deleted the **Resource Group** in Azure.
- Verified all resources were deleted.

<img width="1920" height="939" alt="deleting our stuff" src="https://github.com/user-attachments/assets/25d25258-8c31-4c7f-94b9-93781c2f8a3a" />
<img width="755" height="891" alt="deleting our stuff2" src="https://github.com/user-attachments/assets/90286a1c-45f6-4f5d-a3a1-c17604562a51" />



### Final Reflection
This lab helped me:
- Understand how **network protocols** (ICMP, SSH, DHCP, DNS, RDP) behave.
- Use **Wireshark filters** to capture and study different traffic types.
- See how **Azure NSGs (firewalls)** can block or allow traffic in real time.
- Strengthen my knowledge of how cloud networking works under the hood.

---
