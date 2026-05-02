Switch :
A Network switch is a layer 2 (also layer 3 sometimes) device that connects multiple devices in a LAN and forward data intelligently based on MAC Address.

Internal Components :
Physical Components:
1. Ports (interfaces)
2. ASIC
3. CPU
4. RAM
5. Flash Memory
6. NVRAM
7. Backplane / Switching fabric
8. Power supply

- Real Scenario
PC-A → Port Fa0/1
PC-B → Port Fa0/2

Steps:
Step 1: Frame enters switch

Switch reads:

Source MAC → PC-A
Destination MAC → PC-B
Step 2: Learning

Switch stores:
 “PC-A is on Fa0/1”

Stored in:
MAC Address Table (CAM Table)

Step 3: Forwarding decision

Switch checks:

 “Do I know PC-B?”

Case 1: Unknown

 Flood to all ports

Case 2: Known

 Send only to correct port

Step 4: Reply

PC-B replies → switch learns PC-B

 Now communication becomes direct

 This process is:

 MAC Learning + Forwarding
