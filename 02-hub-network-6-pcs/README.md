# 🌐 Lab 02 — Hub Network with 6 PCs


## 🎯 Objective

Build a simple local network using one hub and six PCs. Configure IPv4 addresses and verify connectivity between the PCs using ICMP ping.

---

## 🗺️ Topology

```text
             PC1
          10.10.10.1
              |
              |
PC2 -------- HUB -------- PC4
10.10.10.2            10.10.10.4
              |
              |
             PC3
          10.10.10.3
            /     \
          PC5     PC6
      10.10.10.5  10.10.10.6
```

---

## 🧰 Devices

* 🔌 1 × Hub
* 💻 6 × PCs
* 🔗 Copper Ethernet cables

---

## 🏷️ IP Addressing

| 🖥️ Device | 📍 IP Address | 🎭 Subnet Mask   |
| --------- | ------------- | ---------------- |
| 💻 PC1    | 10.10.10.1    | 255.255.255.0    |
| 💻 PC2    | 10.10.10.2    | 255.255.255.0    |
| 💻 PC3    | 10.10.10.3    | 255.255.255.0    |
| 💻 PC4    | 10.10.10.4    | 255.255.255.0    |
| 💻 PC5    | 10.10.10.5    | 255.255.255.0    |
| 💻 PC6    | 10.10.10.6    | 255.255.255.0    |

---

## ⚙️ Implementation

1. 🧩 Added one hub and six PCs to Cisco Packet Tracer.
2. 🔌 Connected each PC's FastEthernet interface to the hub.
3. 🔢 Configured a unique IPv4 address on each PC.
4. 🎭 Used `255.255.255.0` as the subnet mask.
5. 📡 Tested connectivity using the `ping` command.

---

## ✅ Verification

Connectivity was tested between the PCs using ICMP.

Example:

```text
ping 10.10.10.2
```

A successful test returned four replies with:

```text
Packets: Sent = 4
Received = 4
Lost = 0 (0% loss)
```

---

## 📚 Key Concepts Learned

* 🔁 Hub-based networking
* 🔢 IPv4 addressing
* 🎭 Subnet masks
* ⚡ FastEthernet
* 📨 ICMP
* 🏓 Ping
* 💥 Collision domains
* 🧱 Layer 1 networking
* 🛠️ Basic network troubleshooting


## 🏆 Skills Practiced

* 🏗️ Building a network topology
* 🔢 Configuring IPv4 addresses
* 📶 Testing connectivity
* 🔍 Reading ping results
* 🛠️ Basic troubleshooting
* 🧠 Understanding hub behavior
