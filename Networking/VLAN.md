\
# VLAN (Virtual Local Area Network) - Zero to Hero

---

# What is a VLAN?

A VLAN (Virtual Local Area Network) is a logical segmentation of a Layer 2 network that divides one physical switch into multiple independent broadcast domains.

A VLAN allows devices to be grouped logically regardless of their physical location.

**Interview Definition**

> A VLAN is a logical segmentation of a Layer 2 network that creates separate broadcast domains on the same physical switch to improve security, scalability, and performance.

---

# Why was VLAN Invented?

Without VLANs:

- Every device belongs to the same broadcast domain.
- Every ARP broadcast reaches every device.
- Security is poor.
- Performance decreases as the network grows.

VLANs solve these problems by isolating broadcast traffic.

---

# Problems Without VLAN

- Large broadcast domain
- Broadcast storms
- Poor security
- Difficult management
- No logical separation of departments

---

# Broadcast Domain vs Collision Domain

## Broadcast Domain

A group of devices that receive Layer 2 broadcasts.

Each VLAN creates one broadcast domain.

## Collision Domain

A portion of the network where collisions can occur.

Each switch port is its own collision domain.

---

# VLAN Example

Physical Switch

```
+---------------------------+
| Fa0/1  HR       VLAN10    |
| Fa0/2  HR       VLAN10    |
| Fa0/3  FIN      VLAN20    |
| Fa0/4  FIN      VLAN20    |
| Fa0/5  IT       VLAN30    |
| Fa0/6  IT       VLAN30    |
+---------------------------+
```

Although only one physical switch exists, it behaves like three separate logical switches.

---

# VLAN Benefits

- Reduces broadcasts
- Improves security
- Better performance
- Easier management
- Logical department separation
- Scalability

---

# VLAN Types

## Default VLAN

By default, all Cisco switch ports belong to VLAN 1.

## Data VLAN

Carries user traffic.

## Voice VLAN

Used for IP Phones.

## Native VLAN

Frames are transmitted untagged across trunk links.

Default: VLAN 1

Best Practice: Change to an unused VLAN (e.g., VLAN 999).

## Management VLAN

Used to manage switches remotely (SSH, Telnet, SNMP).

---

# VLAN ID Range

Normal Range:

1 - 1005

Extended Range:

1006 - 4094

Reserved VLANs:

1002-1005 (Legacy Token Ring/FDDI)

---

# Access Port

An access port belongs to only one VLAN.

Typical Devices:

- PC
- Printer
- Server
- IP Phone

Configuration

```cisco
interface fa0/1
 switchport mode access
 switchport access vlan 10
```

---

# Trunk Port

A trunk carries traffic for multiple VLANs over a single physical link.

Typical Connections:

- Switch to Switch
- Switch to Router
- Switch to Firewall
- Switch to Wireless Controller

Configuration

```cisco
interface g0/1
 switchport mode trunk
```

Allow VLANs

```cisco
switchport trunk allowed vlan 10,20,30
```

---

# IEEE 802.1Q

IEEE 802.1Q is the standard used to tag Ethernet frames with VLAN information.

The switch inserts a VLAN tag before forwarding traffic over a trunk.

PCs never send VLAN tags.

Switches add and remove them.

---

# Access Port vs Trunk Port

| Access Port | Trunk Port |
|-------------|------------|
| One VLAN | Multiple VLANs |
| Untagged Frames | Tagged Frames |
| Connects PCs | Connects Switches/Routers |
| User Port | Infrastructure Port |

---

# Packet Flow

PC1 (VLAN10)

↓

Normal Ethernet Frame

↓

Switch Access Port

↓

Switch identifies VLAN10

↓

Frame leaves Trunk

↓

802.1Q Tag Added

↓

Switch B receives

↓

Reads VLAN Tag

↓

Removes Tag

↓

Forwards to Access Port

↓

Destination PC

---

# CAM Table

Without VLAN

MAC -> Port

With VLAN

VLAN -> MAC -> Port

Example

| VLAN | MAC | Port |
|------|-----|------|
|10|AA-AA-AA|Fa0/1|
|20|BB-BB-BB|Fa0/3|

---

# Can Different VLANs Communicate?

No.

A Layer 2 switch cannot route traffic between VLANs.

Inter-VLAN communication requires:

- Router
OR
- Layer 3 Switch

---

# Native VLAN Mismatch

Example

Switch A

Native VLAN 1

Switch B

Native VLAN 99

Result:

- Wrong VLAN Mapping
- Connectivity Issues
- Security Risks

Verification

```cisco
show interfaces trunk
show cdp neighbors detail
```

---

# Verification Commands

```cisco
show vlan brief

show interfaces trunk

show interfaces switchport

show mac address-table

show running-config
```

---

# Troubleshooting Checklist

- Is VLAN created?
- Is interface UP?
- Correct Access VLAN?
- Trunk UP?
- VLAN allowed on trunk?
- Native VLAN mismatch?
- MAC learned?
- Correct IP subnet?
- Gateway configured?

---

# Common Interview Questions

1. What is VLAN?
2. Why do we need VLAN?
3. Difference between Broadcast and Collision Domain?
4. Difference between Access and Trunk Port?
5. What is IEEE 802.1Q?
6. What is Native VLAN?
7. What happens if Native VLAN mismatches?
8. Why doesn't a PC send VLAN tags?
9. Can two VLANs communicate?
10. Explain packet flow between two switches.
11. Why do we need a trunk?
12. What is Inter-VLAN Routing?

---

# Cisco Configuration Example

```cisco
vlan 10
 name HR

vlan 20
 name Finance

vlan 30
 name IT

interface fa0/1
 switchport mode access
 switchport access vlan 10

interface fa0/2
 switchport mode access
 switchport access vlan 20

interface g0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
 switchport trunk native vlan 999
```

---

# Best Practices

- Do not use VLAN 1 for users.
- Change Native VLAN from VLAN 1.
- Allow only required VLANs on trunks.
- Document VLAN IDs.
- Separate Voice and Data VLANs.
- Use meaningful VLAN names.
- Verify trunks after changes.

---

# Quick Revision

- VLAN = Logical Layer 2 Segmentation
- VLAN creates Broadcast Domains
- Switch Port = Collision Domain
- Access = One VLAN
- Trunk = Multiple VLANs
- IEEE 802.1Q = VLAN Tagging
- Native VLAN = Untagged Traffic
- PCs never tag frames
- Switches add/remove VLAN Tags
- Inter-VLAN requires Router or Layer 3 Switch
- Verify using:
  - show vlan brief
  - show interfaces trunk
  - show mac address-table

