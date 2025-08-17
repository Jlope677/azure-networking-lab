# Azure Networking & Traffic Observation Lab

In this lab, I set up virtual machines in Microsoft Azure, observed different types of network traffic using Wireshark, and experimented with firewall rules. Below is my personal walkthrough and reflections. I’ve also left space for screenshots so I can document the process visually.  

---

## Part 1: Creating Virtual Machines

🔗 [Azure Portal](https://portal.azure.com/)

- Created a **Resource Group** to organize my lab environment.
- Created a **Windows 10 Virtual Machine (VM)** and allowed it to create a **new Virtual Network (VNet)** and **Subnet**.
- Created a **Linux (Ubuntu) VM** in the **same VNet and Subnet** as the Windows VM.
- Used **username/password authentication**.
- Confirmed that both VMs were in the same network so they could communicate.

📸 _[Insert screenshot of Resource Group and VMs here]_

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
- Also pinged a **public website (google.com)** to observe external ICMP traffic.

📸 _[Insert screenshot of Wireshark ICMP capture here]_

### What I Learned
- ICMP packets are how devices communicate using **ping**.
- Internal vs. external traffic looks different in Wireshark.
- Pings confirm whether devices are reachable across a network.

---

## Part 3: Network Security Group (Firewall) & Traffic Types

### 🔒 Blocking ICMP Traffic
- Started a **continuous ping** from Windows → Ubuntu VM.
- Disabled **inbound ICMP traffic** in the Ubuntu VM’s **Network Security Group (NSG)**.
- Observed in Wireshark that ICMP stopped responding.
- Re-enabled ICMP, and pings started working again.

📸 _[Insert screenshot of blocked ICMP traffic here]_

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

📸 _[Insert screenshot of SSH traffic here]_

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

📸 _[Insert screenshot of DHCP traffic here]_

#### What I Learned
- DHCP assigns IPs dynamically.
- You can watch the whole **DISCOVER → OFFER → REQUEST → ACK** handshake in real-time.

---

### 🌐 Observing DNS Traffic
- In Wireshark, filtered for **DNS**.
- Ran:
  ```powershell
  nslookup google.com
  nslookup disney.com
  ```
- Observed DNS queries and responses.

📸 _[Insert screenshot of DNS traffic here]_

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

📸 _[Insert screenshot of RDP traffic here]_

#### What I Learned
- RDP constantly streams desktop updates, so it generates **non-stop traffic**.
- It’s not just when you type or click—everything is live-streamed.

---

## 🔥 Lab Cleanup
- Closed Remote Desktop connection.
- Deleted the **Resource Group** in Azure.
- Verified all resources were deleted.

📸 _[Insert screenshot of Resource Group deletion here]_

### Final Reflection
This lab helped me:
- Understand how **network protocols** (ICMP, SSH, DHCP, DNS, RDP) behave.
- Use **Wireshark filters** to capture and study different traffic types.
- See how **Azure NSGs (firewalls)** can block or allow traffic in real time.
- Strengthen my knowledge of how cloud networking works under the hood.

---
