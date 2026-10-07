# Secure Small Enterprise Network — Cisco Packet Tracer

                    R1
                 /      \
                /        \
              S1          S2
              |            |
            PC-A          PC-B

A small routed enterprise network designed and implemented from scratch using Cisco Packet Tracer.


## Project Overview

This project uses:

- 1 × Cisco 4321 Router (R1)
- 2 × Cisco 2960 Switches (S1 and S2)
- 2 × PCs (PC-A and PC-B)
- IPv4 `/25` subnetting
- Inter-network routing
- Switch management using SVI
- SSH remote management
- RSA keys and local authentication
- Console and VTY security
- Cisco IOS verification commands


## Topology

```text
             R1
          /      \
       S1          S2
       |            |
     PC-A          PC-B
```


R1 provides routing between the two networks.

## IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask | Gateway |
|---|---|---|---|---|
| R1 | G0/0/0 | 192.168.100.1 | 255.255.255.128 | — |
| R1 | G0/0/1 | 192.168.100.129 | 255.255.255.128 | — |
| S1 | VLAN 1 | 192.168.100.2 | 255.255.255.128 | 192.168.100.1 |
| S2 | VLAN 1 | 192.168.100.130 | 255.255.255.128 | 192.168.100.129 |
| PC-A | NIC | 192.168.100.126 | 255.255.255.128 | 192.168.100.1 |
| PC-B | NIC | 192.168.100.254 | 255.255.255.128 | 192.168.100.129 |

## Subnetting

Starting network:

`192.168.100.0/24`

One host bit was borrowed:

`/24 → /25`

This produced two subnets:

### LAN 1 — 192.168.100.0/25

- Network: `192.168.100.0`
- First usable: `192.168.100.1`
- Last usable: `192.168.100.126`
- Broadcast: `192.168.100.127`

### LAN 2 — 192.168.100.128/25

- Network: `192.168.100.128`
- First usable: `192.168.100.129`
- Last usable: `192.168.100.254`
- Broadcast: `192.168.100.255`

## Routing

R1 has both networks as directly connected routes:

```text
C 192.168.100.0/25      directly connected, GigabitEthernet0/0/0
C 192.168.100.128/25    directly connected, GigabitEthernet0/0/1
```

No static route was required because both LANs are directly connected to R1.


## Security Configuration

The network devices were secured using:

- SSH remote management
- RSA key generation
- Local username authentication
- Privilege level 15
- Console passwords
- VTY line security
- Password encryption
- Telnet disabled in favor of SSH

SSH connectivity was successfully tested against:

- R1
- S1
- S2

## Verification

The network was verified using Cisco IOS commands including:

```text
show ip interface brief
show ip route
show ip ssh
show mac address-table
show users
show running-config
show running-config | section line vty
```


Connectivity tests included:

- PC-0 → R1: 0% packet loss
- PC-1 → R1: 0% packet loss
- PC-0 → PC-1: 0% packet loss
- SSH from PC-0 → R1: successful
- SSH from PC-0 → S1: successful
- SSH from PC-1 → S2: successful


## Skills Demonstrated
- IPv4 addressing
- Subnetting
- Network design
- Router configuration
- Switch configuration
- Inter-network routing
- SVI management
- Cisco IOS CLI
- SSH
- RSA authentication
- Network troubleshooting
- Connectivity verification

## Tools
- Cisco Packet Tracer
- Cisco IOS
- IPv4
- SSH

## Project Files

- `packet-tracer/` — place the final `.pkt` project file here
- `configs/` — sanitized configuration examples
- `verification/` — verification notes/output
- `screenshots/` — topology and command screenshots

## Screenshots
| Topology | IP Addressing | PC Connectivity |
| :---: | :---: | :---: |
| <img width="743" alt="Topology" src="https://github.com/user-attachments/assets/d32abbf0-d8bf-4e0e-a941-8a803e85e330" /> | <img width="455" alt="IP Addressing" src="https://github.com/user-attachments/assets/66e571cd-897c-46e8-b69d-081f4268b4c0" /> | <img width="580" alt="PC Connectivity" src="https://github.com/user-attachments/assets/78fc9998-9799-43b9-97e5-9666195e0dea" /> |

| SSH R1 | SSH S1 | SSH S2 |
| :---: | :---: | :---: |
| <img width="622" alt="SSH R1" src="https://github.com/user-attachments/assets/85ca28db-c158-49d1-b323-73a7a7870ee7" /> | <img width="260" alt="SSH S1" src="https://github.com/user-attachments/assets/4dbbbd89-ba20-495b-aa75-fabe5394ab54" /> | <img width="331" alt="SSH S2" src="https://github.com/user-attachments/assets/3dd69bbb-9071-431c-8fb1-1704f54eedb7" /> |

| Routing Table | MAC Address Table |
| :---: | :---: |
| <img width="513" alt="Routing Table" src="https://github.com/user-attachments/assets/0559bdbb-b99a-4f6e-8a68-86622653f2fd" /> | <img width="257" alt="MAC Address Table" src="https://github.com/user-attachments/assets/fabca017-4f4b-4450-af43-b8d630e067ae" /> |


## Future Improvements
Planned extensions to this project include:
- VLAN segmentation
- Inter-VLAN routing
- DHCP
- Access Control Lists (ACLs)
- OSPF dynamic routing
- NAT/PAT
- Additional network security controls
