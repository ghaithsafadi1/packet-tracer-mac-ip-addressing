🔍 Packet Tracer - Identify MAC and IP Addresses
A Cisco Packet Tracer lab exploring how MAC and IP addresses behave during local and remote network communication.

📋 Objectives

Part 1: Gather PDU information for local network communication
Part 2: Gather PDU information for remote network communication


🧠 Background
Understanding how PDUs (Protocol Data Units) travel across networks is fundamental for network administration and security roles. This lab uses Packet Tracer's Simulation Mode to inspect:

Layer 2 (Data Link): MAC address behavior
Layer 3 (Network): IPv4 address behavior

The key insight this lab demonstrates is how addressing changes depending on whether the destination is local (same network) or remote (different network).

🖧 Network Topology
DeviceIP AddressRoleHost A172.16.31.3Source hostHost B172.16.31.2Local destinationHost C10.10.10.2Remote destinationRouter172.16.31.x / 10.10.10.xDefault gateway

🔬 Part 1: Local Network Communication
Scenario: 172.16.31.3 pings 172.16.31.2 (same subnet — no gateway needed)
PDU Capture Table
At DeviceSrc MACDest MACSrc IPv4Dest IPv4172.16.31.30060.7036.2849000C:85CC:1DA7172.16.31.3172.16.31.2(next hop)————
Key Observation

On a local network, the destination MAC address points directly to the target host. No default gateway is involved.


🌐 Part 2: Remote Network Communication
Scenario: 172.16.31.3 pings 10.10.10.2 (different subnet — gateway required)
PDU Capture Table
At DeviceSrc MACDest MACSrc IPv4Dest IPv4172.16.31.30060.7036.284900D0:BA8E:741A172.16.31.310.10.10.2Router (In)——172.16.31.310.10.10.2Router (Out)——172.16.31.310.10.10.210.10.10.2——172.16.31.310.10.10.2
Key Observation

When communicating with a remote network, the destination MAC address is the router's interface MAC — not the final host. The IP addresses remain unchanged throughout the journey, but MAC addresses are rewritten at each hop.


💡 Core Concepts Demonstrated
ConceptLocal CommunicationRemote CommunicationDest. MACTarget host's MACRouter interface MACDest. IPTarget host's IPTarget host's IP (unchanged)Gateway needed?❌ No✅ YesMAC changes at router?N/A✅ Yes — rewritten per hop

🛠️ Tools Used

Cisco Packet Tracer — Network simulation
Simulation Mode — PDU capture and inspection
ICMP ping — Traffic generation


📚 Skills Practiced

Reading OSI Model and PDU Detail tabs in Packet Tracer
Tracing Layer 2 and Layer 3 addressing across hops
Understanding the role of the default gateway in routing
Differentiating local vs. remote network communication behavior


🎓 Part of My Networking Journey
This lab is part of my hands-on networking practice as I work toward the CCST Networking certification through Cisco Skills for All.
Check out my other Packet Tracer labs:

🏠 Home Network Setup
⚙️ DHCP Server Configuration
📐 IPv4 Subnetting


Built with Cisco Packet Tracer | Cisco NetAcad
