# 🌐 Lab 03 — Basic Switch Configuration with 4 PCs

## 🎯 Objective

Build a basic local network using one Cisco switch and four PCs. Configure the switch using the Cisco IOS CLI, assign IPv4 addresses to the PCs, configure a management IP on the switch, and verify connectivity using ICMP ping.

---

## 🗺️ Topology

```text
                         ┌─────────────────┐
                         │       S1        │
                         │     Switch      │
                         │   192.168.1.2   │
                         └─────────────────┘
                           |    |    |    |
                         Fa0/1 Fa0/2 Fa0/3 Fa0/4
                           |    |    |    |
                          PC1  PC2  PC3  PC4
                       .10   .11   .12   .13
```

### Network

```text
Network:      192.168.1.0/24
Subnet Mask:  255.255.255.0
```

---

## 🧰 Devices

* 🔀 1 × Cisco 2960 Switch
* 💻 4 × PCs
* 🔗 Copper Ethernet cables
* 💻 Cisco Packet Tracer

---

## 🏷️ IP Addressing

| 🖥️ Device | 🔌 Switch Port | 📍 IP Address | 🎭 Subnet Mask |
| ---------- | -------------- | ------------- | -------------- |
| 🔀 S1      | VLAN 1         | 192.168.1.2   | 255.255.255.0  |
| 💻 PC1     | Fa0/1          | 192.168.1.10  | 255.255.255.0  |
| 💻 PC2     | Fa0/2          | 192.168.1.11  | 255.255.255.0  |
| 💻 PC3     | Fa0/3          | 192.168.1.12  | 255.255.255.0  |
| 💻 PC4     | Fa0/4          | 192.168.1.13  | 255.255.255.0  |

---

## ⚙️ Implementation

1. 🧩 Added one Cisco 2960 switch and four PCs to Cisco Packet Tracer.
2. 🔌 Connected each PC to a different FastEthernet port on the switch.
3. 🖥️ Configured IPv4 addresses on all four PCs.
4. 🔢 Used `255.255.255.0` as the subnet mask.
5. 🏷️ Changed the switch hostname to `S1`.
6. 🔐 Configured an `enable secret` password.
7. 🖥️ Configured console access.
8. 🌐 Configured VTY lines for remote access.
9. 🔒 Enabled password encryption.
10. 📢 Configured a login banner.
11. 📝 Added descriptions to the switch interfaces.
12. 🟢 Enabled the required switch interfaces using `no shutdown`.
13. 🌐 Configured `VLAN 1` with the management IP `192.168.1.2`.
14. 🔍 Verified the switch configuration.
15. 🏓 Tested connectivity between the PCs using `ping`.
16. 💾 Saved the switch configuration.

---

## 💻 Basic Switch Configuration

### Enter Privileged EXEC Mode

```text
Switch> enable
Switch#
```

### Enter Global Configuration Mode

```text
Switch# configure terminal
Switch(config)#
```

### Configure Hostname

```text
Switch(config)# hostname S1
S1(config)#
```

### Configure Privileged Password

```text
S1(config)# enable secret class123
```

### Configure Console

```text
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login
S1(config-line)# exit
```

### Configure VTY Lines

```text
S1(config)# line vty 0 15
S1(config-line)# password cisco
S1(config-line)# login
S1(config-line)# exit
```

### Enable Password Encryption

```text
S1(config)# service password-encryption
```

### Configure Login Banner

```text
S1(config)# banner motd #Authorized access only!#
```

---

## 🔌 Interface Configuration

### PC1 — Fa0/1

```text
S1(config)# interface fa0/1
S1(config-if)# description PC1
S1(config-if)# no shutdown
S1(config-if)# exit
```

### PC2 — Fa0/2

```text
S1(config)# interface fa0/2
S1(config-if)# description PC2
S1(config-if)# no shutdown
S1(config-if)# exit
```

### PC3 — Fa0/3

```text
S1(config)# interface fa0/3
S1(config-if)# description PC3
S1(config-if)# no shutdown
S1(config-if)# exit
```

### PC4 — Fa0/4

```text
S1(config)# interface fa0/4
S1(config-if)# description PC4
S1(config-if)# no shutdown
S1(config-if)# exit
```

---

## 🌐 Switch Management IP

The management IP was configured on VLAN 1.

```text
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.2 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# exit
```

---

## 🔍 Verification

### Check Interface Status

```text
S1# show ip interface brief
```

The command was used to verify the status of the switch interfaces and the VLAN 1 management interface.

Expected result:

```text
Interface              IP-Address      Status
FastEthernet0/1        unassigned      up
FastEthernet0/2        unassigned      up
FastEthernet0/3        unassigned      up
FastEthernet0/4        unassigned      up
Vlan1                  192.168.1.2     up
```

### Check Running Configuration

```text
S1# show running-config
```

This command was used to verify the active configuration of the switch.

---

## 🏓 Connectivity Test

Connectivity was tested between the PCs using ICMP.

From PC1:

```text
ping 192.168.1.11
```

Additional tests:

```text
ping 192.168.1.12
ping 192.168.1.13
```

A successful test returned:

```text
Packets: Sent = 4
Received = 4
Lost = 0 (0% loss)
```

This confirms that the PCs can communicate through the switch.

---

## 💾 Save Configuration

The switch configuration was saved using:

```text
S1# copy running-config startup-config
```

The configuration was saved so that it can be restored after a switch restart.

---

## 🛠️ Troubleshooting

### Interface is administratively down

Check the interface:

```text
S1# show ip interface brief
```

Enable it:

```text
S1(config)# interface fa0/1
S1(config-if)# no shutdown
```

### PC cannot ping another PC

Check:

* 🔌 Ethernet cable connection
* 🔢 PC IP address
* 🎭 Subnet mask
* 🔌 Correct switch port
* 🟢 Interface status
* ⚙️ `no shutdown`
* 🏷️ Correct network configuration

### Configuration disappears after restart

Save the configuration:

```text
S1# copy running-config startup-config
```

---

## 📚 Key Concepts Learned

* 🔀 Layer 2 switching
* 🖥️ Cisco IOS CLI
* 🧭 CLI configuration modes
* 🏷️ Switch hostname
* 🔐 `enable secret`
* 🖥️ Console access
* 🌐 VTY lines
* 🔒 Password encryption
* 📢 MOTD banner
* 🔌 Switch interfaces
* 📝 Interface descriptions
* 🟢 `no shutdown`
* 🌐 VLAN 1 management interface
* 🔢 IPv4 addressing
* 🎭 Subnet masks
* 📨 ICMP
* 🏓 Ping
* 🔍 Network verification
* 💾 Running vs startup configuration

## 🏆 Skills Practiced

* 🏗️ Building a switch-based LAN topology
* 🖥️ Using Cisco IOS CLI
* ⚙️ Performing basic switch configuration
* 🔌 Configuring switch interfaces
* 🔢 Configuring IPv4 addresses
* 🌐 Configuring a switch management IP
* 🔍 Verifying interface status
* 🏓 Testing network connectivity
* 🛠️ Performing basic troubleshooting
* 💾 Saving network device configurations
* 🧠 Understanding basic Layer 2 switch operation

