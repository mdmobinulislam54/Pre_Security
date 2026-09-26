# OSI Model — Quick Notes

The **OSI (Open Systems Interconnection) model** is a 7-layer conceptual framework that explains how data moves through a network.

### 🔹 7 Layers of OSI

| Layer | Name         | Main Function                             | Examples                 |
| ----- | ------------ | ----------------------------------------- | ------------------------ |
| **7** | Application  | Network services for applications         | HTTP, DNS, FTP, SMTP     |
| **6** | Presentation | Encoding, encryption, compression         | JPEG, PNG, MIME, Unicode |
| **5** | Session      | Establishes & manages sessions            | NFS, RPC                 |
| **4** | Transport    | End-to-end communication & segmentation   | TCP, UDP                 |
| **3** | Network      | IP addressing & routing                   | IP, ICMP, IPSec          |
| **2** | Data Link    | Communication within the same network     | Ethernet, Wi-Fi, MAC     |
| **1** | Physical     | Transmits raw bits through physical media | Cable, Fibre, Radio      |

### 🧠 Mnemonic

**Please Do Not Throw Spinach Pizza Away**

**P**hysical → **D**ata Link → **N**etwork → **T**ransport → **S**ession → **P**resentation → **A**pplication

### Key Points

* **Layer 1:** Bits & physical signals
* **Layer 2:** MAC addresses & frames
* **Layer 3:** IP addresses & routing
* **Layer 4:** TCP/UDP & end-to-end communication
* **Layer 5:** Sessions
* **Layer 6:** Encoding, encryption & compression
* **Layer 7:** Application-level network protocols


# TCP/IP Model — Quick Notes

The **TCP/IP model** is an implemented networking model used for communication over the Internet. It was developed in the **1970s by the U.S. Department of Defense (DoD)**.

### 🔹 TCP/IP Model — 4 Layers

| Layer           | OSI Equivalent | Main Function                                       | Examples                         |
| --------------- | -------------- | --------------------------------------------------- | -------------------------------- |
| **Application** | OSI 5, 6, 7    | Application services, data formatting & sessions    | HTTP, HTTPS, FTP, DNS, SSH, SMTP |
| **Transport**   | OSI 4          | End-to-end communication                            | TCP, UDP                         |
| **Internet**    | OSI 3          | IP addressing & routing                             | IP, ICMP, IPSec                  |
| **Link**        | OSI 1, 2       | Local network communication & physical transmission | Ethernet, Wi-Fi                  |

### 🧠 OSI → TCP/IP

**OSI 7 + 6 + 5 → Application**
**OSI 4 → Transport**
**OSI 3 → Internet**
**OSI 2 + 1 → Link**

### 🔹 5-Layer Version

Some textbooks divide the Link layer into two:

**Application → Transport → Network → Link → Physical**

### Key Point

The **OSI model has 7 layers**, while the commonly used **TCP/IP model has 4 layers** (or **5 layers** when Physical is separated).


# IP Addresses — Quick Notes

An **IP address** uniquely identifies a device on a network and allows devices to communicate.

## IPv4

* IPv4 = **32 bits**
* Divided into **4 octets (bytes)**
* Each octet ranges from **0–255**
* Example: `192.168.1.10`
* Maximum theoretical addresses: **2³² ≈ 4.3 billion**

### Network & Broadcast

For a typical `/24` network:

* **Network address:** `192.168.1.0`
* **Usable hosts:** `192.168.1.1 – 192.168.1.254`
* **Broadcast address:** `192.168.1.255`

## Subnet Mask / CIDR

`255.255.255.0` = **`/24`**

`/24` means the first **24 bits** identify the network, leaving **8 bits** for hosts.

Example:

```text
192.168.66.89/24
Network:   192.168.66.0
Broadcast: 192.168.66.255
Hosts:     192.168.66.1 – 192.168.66.254
```

### Useful Commands

**Windows:**

```bash
ipconfig
```

**Linux:**

```bash
ifconfig
ip address show
ip a s
```

## Private IP Ranges

| Range                           | CIDR         |
| ------------------------------- | ------------ |
| `10.0.0.0 – 10.255.255.255`     | `10/8`       |
| `172.16.0.0 – 172.31.255.255`   | `172.16/12`  |
| `192.168.0.0 – 192.168.255.255` | `192.168/16` |

Private IPs are used inside local networks and normally access the Internet through **NAT**.

## Routing

A **router operates at Layer 3 (Network Layer)**.

It examines the destination **IP address** and forwards packets toward the appropriate network. A packet may pass through multiple routers before reaching its destination.

### 🧠 Remember

* **IP = Logical address**
* **MAC = Layer 2 hardware address**
* **Router = Layer 3**
* **IPv4 octet = 0–255**
* **Private IP ≠ Public IP**
* **`/24` = `255.255.255.0`**



# TCP & UDP — Quick Notes

Both **TCP and UDP** operate at **Layer 4 (Transport Layer)** and use **port numbers** to identify processes/applications.

## UDP — User Datagram Protocol

* **Connectionless**
* No connection establishment
* No delivery confirmation
* Faster and lightweight
* Uses **port numbers**
* Port range: **1–65,535**
* Suitable when speed is more important than reliability

**Example:** Like sending standard mail without delivery confirmation.

## TCP — Transmission Control Protocol

* **Connection-oriented**
* Reliable data delivery
* Uses sequence numbers and acknowledgements
* Detects lost or duplicated data
* Requires a **3-way handshake**
* Uses **port numbers**
* Port range: **1–65,535**

### TCP 3-Way Handshake

```text
Client                    Server
  |                         |
  | ------ SYN ----------> |
  | <---- SYN + ACK ------ |
  | ------ ACK ----------> |
  |                         |
       Connection Ready
```

### 🧠 Remember

**UDP → Fast + Connectionless + No guarantee**

**TCP → Reliable + Connection-oriented + 3-way handshake**

**TCP/UDP → Layer 4**

**Port numbers → 1–65,535**



# Encapsulation — Quick Notes

**Encapsulation** is the process where each network layer adds its own **header** (and sometimes a trailer) to data before passing it to the next layer.

### 📦 Data Encapsulation

```text
Application Data
       ↓
TCP Segment / UDP Datagram
       ↓
IP Packet
       ↓
Wi-Fi / Ethernet Frame
```

| Layer       | Data Unit          | What Happens                      |
| ----------- | ------------------ | --------------------------------- |
| Application | Data               | Original application data         |
| Transport   | Segment / Datagram | TCP or UDP header added           |
| Internet    | Packet             | IP header added                   |
| Link        | Frame              | Link-layer header + trailer added |

### 🔄 Decapsulation

At the destination, the process is reversed. Each layer removes its corresponding header/trailer until the original application data is recovered.

### 🧠 Remember

**Data → Segment/Datagram → Packet → Frame**

* **TCP → Segment**
* **UDP → Datagram**
* **IP → Packet**
* **Wi-Fi/Ethernet → Frame**


# Telnet — Quick Notes

**Telnet (Teletype Network)** is a protocol and command-line client used to establish a **TCP connection** to a remote system.

It can connect to any service listening on a TCP port and allows us to communicate with it using text.

### Basic Syntax

```bash
telnet MACHINE_IP PORT
```

### Common Examples

**Echo server — Port 7**

```bash
telnet MACHINE_IP 7
```

Anything you send is returned by the server.

**Daytime server — Port 13**

```bash
telnet MACHINE_IP 13
```

Returns the current date and time.

**HTTP server — Port 80**

```bash
telnet MACHINE_IP 80
```

Then send an HTTP request:

```http
GET / HTTP/1.1
Host: telnet.thm
```

Press **Enter twice** to send the request.

### Key Points

* Telnet operates over **TCP**.
* It can be used to test and interact with TCP services.
* **Port 23** is the traditional Telnet remote-login port.
* Telnet is **insecure for remote administration** because it sends data, including credentials, in plaintext.
* For secure remote administration, **SSH** is preferred.

### Useful Commands

Exit Telnet:

```text
Ctrl + ]
```

Then:

```text
quit
```

### 🧠 Remember

**Telnet = TCP connection + text-based communication**

It is useful for understanding how network protocols communicate at the TCP level.
