# WK1-PM1: Cybersecurity Testing Lab Environment Setup

## Project Overview
This project involves setting up a professional cybersecurity testing lab environment on a local PC using Oracle VirtualBox and Kali Linux as the attacking machine, configured with custom networking, shared folders, and host integration features[cite: 3, 4, 7, 8].

---

## Step-by-Step Implementation & Screenshots

### 1. NAT Network Configuration
Configured a dedicated `NATNetwork` in VirtualBox Manager using the required subnet `10.0.0.0/24` with DHCP enabled[cite: 3].
* **Screenshot:** `Screenshot 2026-10-29 153707.png`  
![NAT Network Setup](Screenshot%202026-10-29%20153707.png)[cite: 3]

### 2. Virtual Machine Network Settings
Attached the Kali Linux VM Network Adapter 1 to the custom `NATNetwork` with Promiscuous Mode set to "Allow All"[cite: 4].
* **Screenshot:** `Screenshot 2026-10-29 153506.png`  
![VM Network Adapter](Screenshot%202026-10-29%20153506.png)[cite: 4]

### 3. System Resources Setup
Configured system base memory and acceleration settings for optimal performance[cite: 5, 6].
* **Screenshot:** `Screenshot 2026-10-30 053230.png`  
![System Settings](Screenshot%202026-10-30%20053230.png)[cite: 5]
* **Screenshot:** `Screenshot 2026-10-30 053342.png`  
![System Acceleration](Screenshot%202026-10-30%20053342.png)[cite: 6]

### 4. Shared Folders & Host Integration
Configured shared folders linking the host directory (`C:\kali`) to the Kali Linux guest environment, alongside clipboard and drag-and-drop integration[cite: 7, 8].
* **Screenshot:** `Screenshot 2026-10-30 053513.png`  
![Shared Folders Config](Screenshot%202026-10-30%20053513.png)[cite: 7]
* **Screenshot:** `Screenshot 2026-10-30 055107.jpg`  
![Kali Desktop Integration](Screenshot%202026-10-30%20055107.jpg)[cite: 8]

---

## Troubleshooting Experience

### Problem Faced:
During initial configuration, testing network connectivity yielded a `Temporary failure in name resolution` error and `Destination Host Unreachable` messages when pinging the default gateway (`10.0.0.1`) and external IP addresses (`8.8.8.8`), even though the NAT network was active[cite: 10, 11, 12]. 

* **Troubleshooting Screenshots:**
  * `Screenshot 2026-10-29 091819.jpg` (Network Manager restart phase)
  * `Screenshot 2026-10-29 091943.png` (Name resolution and unreachable gateway errors)[cite: 11]
  * `Screenshot 2026-10-29 092019.png` (Checking route table via `ip route`)

### Solution:
1. Restarted the NetworkManager service inside Kali Linux using terminal commands to refresh the active network adapter connection (`sudo nmcli networking off` followed by `sudo nmcli networking on`).
2. Verified the routing table using `ip route` to ensure traffic correctly routed through `eth0` via gateway `10.0.0.1`[cite: 10, 12].
3. Successfully re-tested connectivity with ping commands, confirming full internet and network access.

* **Successful Connection Screenshot:** `Screenshot 2026-10-29 095226.jpg`  
![Successful Ping Test](Screenshot%202026-10-29%20095226.jpg)[cite: 9]
