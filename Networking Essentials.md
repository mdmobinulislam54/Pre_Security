# DHCP — Quick Notes

**DHCP (Dynamic Host Configuration Protocol)** automatically provides devices with the network configuration they need to communicate.

It can provide:

* **IP address**
* **Subnet mask**
* **Default gateway**
* **DNS server**

### 🔹 DHCP Details

* **Protocol:** UDP
* **DHCP Server:** UDP **67**
* **DHCP Client:** UDP **68**

### 🔄 DORA Process

DHCP uses **4 steps**, known as **DORA**:

```text
1. Discover  → Client searches for a DHCP server
2. Offer     → Server offers an IP address
3. Request   → Client requests the offered IP
4. Acknowledge → Server confirms the assignment
```

### 📡 Initial DHCP Communication

Before receiving an IP address, the client uses:

```text
Source IP:      0.0.0.0
Destination IP: 255.255.255.255
```

The client also sends the DHCP Discover to the broadcast MAC address:

```text
ff:ff:ff:ff:ff:ff
```

### 🧠 Answers

**1. How many steps does DHCP use?**
→ **4**

**2. Destination IP for DHCP Discover?**
→ **255.255.255.255**

**3. Source IP before receiving configuration?**
→ **0.0.0.0**

### 🧠 Remember

**DORA = Discover → Offer → Request → Acknowledge**

**DHCP = Automatic network configuration**



# ARP — Quick Notes

**ARP (Address Resolution Protocol)** is used to find the **MAC address associated with an IP address** on the local network.

### 🔹 Why ARP?

A device may know the destination's **IP address**, but to send an Ethernet/Wi-Fi frame on the local network, it needs the destination's **MAC address**.

```text
IP Address (Layer 3)
        ↓
       ARP
        ↓
MAC Address (Layer 2)
```

### 🔄 ARP Process

**1. ARP Request**

The sender broadcasts:

```text
Who has 192.168.66.1?
```

Destination MAC:

```text
ff:ff:ff:ff:ff:ff
```

**2. ARP Reply**

The target responds with its MAC address:

```text
192.168.66.1 is at 44:df:65:d8:fe:6c
```

### 📦 Important Points

* ARP maps **IP → MAC**
* ARP Request → **Broadcast**
* ARP Reply → **Unicast** to the requester
* ARP is carried **directly inside an Ethernet frame**
* It does **not** use TCP, UDP, or IP for the ARP message itself.

### 🧠 Answers

**1. Destination MAC address in an ARP Request:**
`ff:ff:ff:ff:ff:ff`

**2. MAC address of `192.168.66.1`:**
`44:df:65:d8:fe:6c`

### 🧠 Remember

**ARP = "I know the IP, but what's the MAC?"**



# Routing Protocols — Quick Notes

**Routing protocols** help routers determine the best path for forwarding packets between different networks.

### 🔹 Common Routing Protocols

| Protocol  | Full Form                                  | Key Point                                                   |
| --------- | ------------------------------------------ | ----------------------------------------------------------- |
| **OSPF**  | Open Shortest Path First                   | Uses network topology to calculate efficient paths          |
| **EIGRP** | Enhanced Interior Gateway Routing Protocol | **Cisco proprietary** routing protocol                      |
| **BGP**   | Border Gateway Protocol                    | Main routing protocol used between networks on the Internet |
| **RIP**   | Routing Information Protocol               | Uses hop count to select routes                             |

### 🧠 Remember

* **OSPF → Shortest/best path**
* **EIGRP → Cisco**
* **BGP → Internet / inter-network routing**
* **RIP → Hop count**

**Answer:** Cisco proprietary → **EIGRP**




# NAT — Quick Notes

**NAT (Network Address Translation)** allows multiple devices with **private IP addresses** to access the Internet using a **single public IP address**.

### 🔹 Why NAT?

IPv4 addresses are limited. NAT helps reduce the need for public IPv4 addresses.

```text
Private Network                  Internet
192.168.0.129 ─┐
192.168.0.130 ─┼──> NAT Router ──> 212.3.4.5
192.168.0.131 ─┘
```

All devices can appear on the Internet as:

**`212.3.4.5`**

### 🔄 How NAT Works

The NAT router maintains a **translation table** that maps:

```text
Private IP + Port  ↔  Public IP + Port
```

Example:

```text
192.168.0.129:15401
        ↓ NAT
212.3.4.5:19273
```

The external web server sees `212.3.4.5:19273`, not the private IP.

### 🔹 TCP Connections

TCP uses port numbers from **1–65,535**.

Therefore, with one public IP and assuming unlimited processing capacity, approximately:

**65 thousand simultaneous TCP connections**

can be distinguished by source ports.

### 🧠 Remember

* **NAT = Private IP → Public IP translation**
* Multiple devices can share **one public IP**
* NAT maintains a **translation table**
* **IP + Port** identifies a connection
* Approx. **65K TCP connections per public IP/port space**
