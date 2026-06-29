# 🌐 Network Engineering Zero to Hero 🚀

# 🎯 Interview Questions

---

# Q1. What is Networking?

## Answer

Networking is the process of connecting two or more devices so they can communicate and exchange information.

A network allows devices to:

- Exchange data
- Share resources
- Access the Internet
- Access servers
- Share printers
- Use cloud applications
- Communicate securely

### Interview Answer

> A computer network is a collection of interconnected devices that communicate with each other using networking protocols to exchange data and share resources.

---

# Q2. Why do we need Networking?

## Answer

Without networking, computers work independently and cannot communicate with each other.

Networking enables:

- Communication
- Resource Sharing
- Internet Access
- Email
- Video Conferencing
- Database Access
- File Sharing
- Cloud Connectivity
- Centralized Management

### Interview Answer

> Networking enables communication between devices, resource sharing, centralized management, internet connectivity, and secure collaboration.

---

# Q3. Why can't every computer connect directly to every other computer?

## Answer

Direct connections between every device are not scalable.

For example:

- 10 computers require many cables.
- 100 computers require thousands of cables.

This creates:

- High Cost
- Difficult Management
- Complex Troubleshooting
- Poor Scalability

To solve this problem, switches were introduced.

Instead of connecting every computer to every other computer, every device connects to a central switch.

### Interview Answer

> Direct device-to-device communication is not scalable. Switches simplify connectivity by acting as a centralized communication device.

---

# Q4. What are the three basic requirements for communication?

## Answer

Every communication requires:

1. Source Address
2. Destination Address
3. Path

Without these three components, communication is impossible.

---

# Q5. What is a MAC Address?

## Answer

MAC stands for **Media Access Control**.

A MAC Address is a unique Layer-2 hardware address assigned to every Network Interface Card (NIC).

Example:

```
00:1A:2B:3C:4D:5E
```

Characteristics:

- Layer 2 Address
- Physical Address
- Used by Switches
- Usually Manufacturer Assigned

### Interview Answer

> A MAC address is a unique Layer-2 hardware address used for communication within the same local network.

---

# Q6. What is an IP Address?

## Answer

An IP Address is a logical Layer-3 address assigned to every network device.

Unlike a MAC Address, an IP Address can change.

Example:

```
192.168.1.10
```

Used for communication between different networks.

### Interview Answer

> An IP Address is a logical Layer-3 address used for identifying devices and routing packets across networks.

---

# Q7. Difference between MAC Address and IP Address

| MAC Address | IP Address |
|-------------|------------|
| Physical Address | Logical Address |
| Layer 2 | Layer 3 |
| Used by Switch | Used by Router |
| Local Communication | Inter-Network Communication |
| Usually Permanent | Can Change |

---

# Q8. What is ARP?

## Answer

ARP (Address Resolution Protocol) is used to map an IPv4 address to a MAC Address within a local network.

If a device knows the destination IP but does not know the destination MAC, it sends an ARP Request.

The device owning that IP replies with its MAC Address.

### Interview Answer

> ARP resolves an IPv4 address into a MAC Address for communication within the same LAN.

---

# Q9. Why is ARP Needed?

## Answer

Applications communicate using IP Addresses, but Ethernet communication requires MAC Addresses.

ARP bridges the gap between Layer 3 (IP) and Layer 2 (MAC).

Without ARP, devices cannot communicate over Ethernet.

---

# Q10. Is ARP Request Broadcast or Unicast?

## Answer

ARP Request → Broadcast

```
FF:FF:FF:FF:FF:FF
```

ARP Reply → Unicast

Only the requesting device receives the reply.

### Interview Answer

> ARP Request is Broadcast, whereas ARP Reply is Unicast.

---

# Q11. Why does a PC ARP for the Gateway instead of the Internet Server?

## Answer

If the destination is outside the local subnet, the PC does not need the destination server's MAC Address.

Instead, it needs the MAC Address of the Default Gateway.

The router then forwards the packet towards the destination network.

### Interview Answer

> A host ARPs for the Default Gateway's MAC Address when communicating with remote networks because the router is responsible for forwarding packets outside the local subnet.

---

# Q12. Do MAC Addresses change during packet travel?

## Answer

Yes.

Every time a packet passes through a router, the Ethernet Frame is rebuilt.

The Source and Destination MAC Addresses change at every hop.

The Source and Destination IP Addresses remain the same throughout the journey (unless NAT is performed).

### Interview Answer

> MAC Addresses change at every Layer-2 hop, while IP Addresses remain end-to-end.

---

# Q13. What is a Switch?

## Answer

A Switch is a Layer-2 networking device that connects multiple devices within the same Local Area Network (LAN).

It forwards Ethernet Frames based on MAC Addresses using a CAM Table.

### Interview Answer

> A Switch is a Layer-2 device that forwards Ethernet Frames using MAC Addresses learned in its CAM Table.

---

# Q14. How does a Switch learn MAC Addresses?

## Answer

A Switch learns MAC Addresses automatically by examining the Source MAC Address of every incoming Ethernet Frame.

The Switch stores this information in the CAM Table.

Example:

| MAC Address | Interface |
|-------------|-----------|
| AA-AA-AA-AA-AA-AA | Fa0/1 |

This process is known as MAC Learning.

### Interview Answer

> A Switch learns MAC Addresses by reading the Source MAC Address of incoming frames and storing the mapping in the CAM Table.

---

# Q15. Why does a Switch learn from the Source MAC instead of the Destination MAC?

## Answer

The Source MAC belongs to the device physically connected to the incoming interface.

The Destination MAC only indicates where the sender wants to send the frame and does not reveal where that destination device is connected.

Therefore, the Switch learns only from the Source MAC.

### Interview Answer

> Switches learn from the Source MAC because it accurately identifies the device connected to the incoming interface.

---

# Q16. What happens if the Destination MAC is unknown?

## Answer

The Switch first learns the Source MAC.

It then checks its CAM Table for the Destination MAC.

If the Destination MAC is not found, the Switch performs Unknown Unicast Flooding by forwarding the frame out of all ports except the incoming port.

When the destination replies, the Switch learns its MAC Address and future traffic is forwarded directly.

### Interview Answer

> If the Destination MAC is unknown, the Switch floods the frame to all interfaces except the incoming interface.

---

# Q17. What is a CAM Table?

## Answer

CAM stands for **Content Addressable Memory**.

The CAM Table stores MAC-to-Port mappings learned by the Switch.

Example:

| MAC Address | Interface |
|-------------|-----------|
| AA-AA-AA-AA-AA-AA | Fa0/1 |
| BB-BB-BB-BB-BB-BB | Fa0/2 |

Cisco Command:

```bash
show mac address-table
```

---

# Q18. What is Flooding?

## Answer

Flooding occurs when the Switch does not know the Destination MAC Address.

The frame is forwarded to every port except the incoming port.

Once the destination responds, flooding no longer occurs because the MAC Address has been learned.

---

# Q19. What is the difference between Flooding and Broadcasting?

| Flooding | Broadcasting |
|-----------|--------------|
| Happens when Destination MAC is Unknown | Happens when Destination MAC is FF:FF:FF:FF:FF:FF |
| Switch decision | Sender decision |
| Temporary | Intentional |

---

# Q20. Does a Switch require VLANs to learn MAC Addresses?

## Answer

No.

A Switch can learn MAC Addresses even without VLAN configuration.

By default, all switch ports belong to VLAN 1.

When VLANs are configured, the CAM Table stores MAC Addresses along with their associated VLAN IDs.

Example:

| VLAN | MAC Address | Interface |
|------|-------------|-----------|
| 10 | AA-AA-AA-AA-AA-AA | Fa0/1 |
| 20 | BB-BB-BB-BB-BB-BB | Fa0/2 |

### Interview Answer

> VLANs are not required for MAC Learning. Switches learn MAC Addresses regardless of VLAN configuration. VLANs simply separate the MAC table entries into different broadcast domains.
