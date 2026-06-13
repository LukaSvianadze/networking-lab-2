# Cisco Packet Tracer — Full Network Lab
**Author:** Luka Svianadze

A complete enterprise network simulation built in Cisco Packet Tracer covering VLANs, Inter-VLAN routing, OSPF, and a three-layer hierarchical network design (Access, Distribution, Core).

---

## IP Addressing Table

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| R1 | Se0/1/0 | 10.0.0.1 | 255.255.255.252 |
| R1 | Se0/1/1 | 10.0.0.5 | 255.255.255.252 |
| R2 | Se0/0/0 | 10.0.0.2 | 255.255.255.252 |
| R2 | Gig0/0 | 172.16.1.1 | 255.255.255.252 |
| R3 | Se0/1/0 | 10.0.0.6 | 255.255.255.252 |
| R3 | Gig0/0 | 172.16.2.1 | 255.255.255.252 |
| SW1 | Fa0/24 (routed) | 172.16.1.2 | 255.255.255.252 |
| SW1 | VLAN 10 SVI | 192.168.10.1 | 255.255.255.0 |
| SW1 | VLAN 20 SVI | 192.168.20.1 | 255.255.255.0 |
| SW2 | Fa0/24 (routed) | 172.16.2.2 | 255.255.255.252 |
| SW2 | VLAN 30 SVI | 192.168.30.1 | 255.255.255.0 |
| SW2 | VLAN 40 SVI | 192.168.40.1 | 255.255.255.0 |
| PC0 | NIC | 192.168.10.10 | 255.255.255.0 |
| PC2 | NIC | 192.168.20.10 | 255.255.255.0 |
| PC4 | NIC | 192.168.30.10 | 255.255.255.0 |
| PC7 | NIC | 192.168.40.20 | 255.255.255.0 |

---

## VLAN Table

| VLAN ID | Name | Department | Subnet |
|---|---|---|---|
| 10 | HR | Human Resources | 192.168.10.0/24 |
| 20 | IT | Information Technology | 192.168.20.0/24 |
| 30 | Sales | Sales | 192.168.30.0/24 |
| 40 | Finance | Finance | 192.168.40.0/24 |

---

## Devices Used

| Device | Model | Role | Layer |
|---|---|---|---|
| R1, R2, R3 | Cisco 2911 | Routing / WAN | Layer 3 |
| SW1, SW2 | Cisco 3560-24PS | Distribution | Layer 3 |
| SW3, SW4, SW5, SW6 | Cisco 2960-24TT | Access | Layer 2 |
| PC0–PC7 | Generic PC | End devices | — |

---

## Topics Covered

- IP addressing and subnetting (/24, /30)
- VLAN creation and assignment
- Trunk ports (802.1Q)
- Inter-VLAN routing using Layer 3 switch SVIs
- Three-layer hierarchical network design (Access, Distribution, Core)
- OSPF (Open Shortest Path First) — single Area 0
- Serial WAN links with clock rate
- Routed ports on Layer 3 switches (`no switchport`)

---

## How to Open

1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) (free with a Cisco NetAcad account)
2. Clone or download this repository
3. Open the `.pkt` file in Packet Tracer
4. All configurations are pre-loaded and ready

---

## Verification

All the following were verified and working:

```
PC0 (VLAN10) ping PC2 (VLAN20)  ✓  inter-VLAN routing on SW1
PC0 (VLAN10) ping PC4 (VLAN30)  ✓  full path across OSPF network
PC0 (VLAN10) ping PC7 (VLAN40)  ✓  full path across OSPF network
show ip ospf neighbor            ✓  all neighbors in FULL state
show ip route                   ✓  all networks visible via OSPF (O)
```

---

## Key Commands Reference

```bash
# Verify OSPF neighbors
show ip ospf neighbor

# Verify routing table
show ip route

# Verify VLANs
show vlan brief

# Verify trunk ports
show interfaces trunk

# Verify interface status
show ip interface brief
```

---

*Built as part of CCNA self-study practice.*
