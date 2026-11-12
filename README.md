# IPv6 Router-on-a-Stick Inter-VLAN Routing

## Project Overview

This project demonstrates the implementation of Router-on-a-Stick Inter-VLAN Routing using IPv6 in Cisco Packet Tracer.

A single router (RA) is configured with multiple sub-interfaces to enable communication between different VLANs through an IEEE 802.1Q trunk connection.

The project also implements VLAN segmentation, Native VLAN configuration, and unused switch port security.

## Network Devices

- 1 Cisco Router (RA)
- 1 Cisco Switch (SWA)
- End devices (PCs) assigned to different VLANs

## VLAN Configuration

| VLAN ID | VLAN Name | Purpose |
|---|---|---|
| 11 | Admin | Administration department |
| 22 | Accounts | Accounts department |
| 33 | HR | Human Resources department |
| 35 | Native | Native VLAN |
| 44 | Unused | Unused switch ports |

## IPv6 Addressing Scheme

| Department | VLAN | IPv6 Address | Default Gateway |
|---|---:|---|---|
| Admin | 11 | 2001:DB8:ACAD:11::F/64 | FE80::1 |
| Accounts | 22 | 2001:DB8:ACAD:22::F/64 | FE80::1 |
| HR | 33 | 2001:DB8:ACAD:33::F/64 | FE80::1 |

## Router Configuration (RA)

The router uses sub-interfaces to provide routing between VLANs.

- G0/0/1.11 – Admin VLAN
- G0/0/1.22 – Accounts VLAN
- G0/0/1.33 – HR VLAN
- G0/0/1.35 – Native VLAN

IEEE 802.1Q encapsulation is configured on the sub-interfaces.

IPv6 routing is enabled using:

```bash
ipv6 unicast-routing
```

The router uses FE80::1 as the link-local default gateway for the departmental VLANs.

## Switch Configuration (SWA)

The switch is configured with five VLANs.

Access ports:

- Fa0/1–Fa0/6: Admin (VLAN 11)
- Fa0/7–Fa0/12: Accounts (VLAN 22)
- Fa0/13–Fa0/18: HR (VLAN 33)

Trunk configuration:

- Interface: G0/1
- Native VLAN: 35
- Allowed VLANs: 11, 22, 33, 35

## Switch Port Security and Management

Unused switch ports are assigned to VLAN 44 and administratively disabled.

The `switchport nonegotiate` command is configured to disable DTP negotiation on the unused ports.

## Verification Commands

### Router

```bash
show ipv6 interface brief
```

### Switch

```bash
show vlan brief
show interfaces trunk
```

Additional connectivity testing can be performed using:

```bash
ping 2001:DB8:ACAD:22::F
ping 2001:DB8:ACAD:33::F
```

## Key Learning Outcomes

- Configuring IPv6 addressing on Cisco routers.
- Implementing Router-on-a-Stick Inter-VLAN Routing.
- Creating and managing VLANs.
- Configuring IEEE 802.1Q trunk links.
- Configuring Native VLANs.
- Understanding IPv6 link-local addresses.
- Disabling DTP negotiation.
- Securing unused switch ports.
- Verifying VLAN and trunk configurations.

## Tools Used

- Cisco Packet Tracer
- Cisco IOS CLI
- IPv6
- IEEE 802.1Q

## Conclusion

This project provides practical experience in configuring IPv6-based inter-VLAN routing and managing a segmented enterprise network using Cisco networking devices.
