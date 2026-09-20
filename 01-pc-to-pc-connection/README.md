
# Lab 01 — Direct PC-to-PC Connection

## Objective

Build a simple network connecting two PCs directly using a Copper Cross-Over cable and verify connectivity using the `ping` command.

## Topology

```text
PC1                              PC2
10.0.0.1                         10.0.0.2
   |                                |
   └──── Copper Cross-Over ─────────┘
```

## Configuration

| Device | Interface    | IP Address | Subnet Mask   |
| ------ | ------------ | ---------- | ------------- |
| PC1    | FastEthernet | 10.0.0.1   | 255.255.255.0 |
| PC2    | FastEthernet | 10.0.0.2   | 255.255.255.0 |

## Verification

From PC1, I tested connectivity using:

```text
ping 10.0.0.2
```

Result:

```text
Packets: Sent = 4
Received = 4
Lost = 0 (0% loss)
```

The successful ping confirms that PC1 and PC2 can communicate correctly over the direct Ethernet connection.

## Technologies / Concepts

* Cisco Packet Tracer
* IPv4 addressing
* FastEthernet
* Copper Cross-Over cable
* ICMP
* Ping
* Basic network troubleshooting

## What I Learned

This lab helped me understand how two end devices can communicate directly using Ethernet and IPv4 addressing. I also learned how to verify connectivity using ICMP ping and interpret packet loss and response information.
