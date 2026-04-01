# 🔍 Packet Tracer - Identify MAC and IP Addresses

A Cisco Packet Tracer lab exploring how MAC and IP addresses behave during local and remote network communication.

---

## 📋 Objectives

- **Part 1:** Gather PDU information for local network communication
- **Part 2:** Gather PDU information for remote network communication

---

## 🧠 Background

Understanding how PDUs (Protocol Data Units) travel across networks is fundamental for network administration and security roles. This lab uses Packet Tracer's **Simulation Mode** to inspect:

- **Layer 2 (Data Link):** MAC address behavior
- **Layer 3 (Network):** IPv4 address behavior

The key insight this lab demonstrates is how addressing changes depending on whether the destination is **local** (same network) or **remote** (different network).

---

## 🖧 Network Topology

| Device | IP Address | Role |
|--------|-----------|------|
| Host A | 172.16.31.3 | Source host |
| Host B | 172.16.31.2 | Local destination |
| Host C | 10.10.10.2 | Remote destination |
| Router | 172.16.31.x / 10.10.10.x | Default gateway |

---

## 🔬 Part 1: Local Network Communication

**Scenario:** `172.16.31.3` pings `172.16.31.2` (same subnet — no gateway needed)

### PDU Capture Table

| At Device | Src MAC | Dest MAC | Src IPv4 | Dest IPv4 |
|-----------|---------|----------|----------|-----------|
| 172.16.31.3 | 0060.7036.2849 | 000C:85CC:1DA7 | 172.16.31.3 | 172.16.31.2 |
| *(next hop)* | — | — | — | — |

### Key Observation
> On a local network, the **destination MAC address points directly to the target host**. No default gateway is involved.

---

## 🌐 Part 2: Remote Network Communication

**Scenario:** `172.16.31.3` pings `10.10.10.2` (different subnet — gateway required)

### PDU Capture Table

| At Device | Src MAC | Dest MAC | Src IPv4 | Dest IPv4 |
|-----------|---------|----------|----------|-----------|
| 172.16.31.3 | 0060.7036.2849 | 00D0:BA8E:741A | 172.16.31.3 | 10.10.10.2 |
| Router (In) | — | — | 172.16.31.3 | 10.10.10.2 |
| Router (Out) | — | — | 172.16.31.3 | 10.10.10.2 |
| 10.10.10.2 | — | — | 172.16.31.3 | 10.10.10.2 |

### Key Observation
> When communicating with a **remote network**, the destination MAC address is the **router's interface MAC** — not the final host. The IP addresses remain unchanged throughout the journey, but MAC addresses are rewritten at each hop.

---

## 💡 Core Concepts Demonstrated

| Concept | Local Communication | Remote Communication |
|---------|--------------------|--------------------|
| Dest. MAC | Target host's MAC | Router interface MAC |
| Dest. IP | Target host's IP | Target host's IP (unchanged) |
| Gateway needed? | ❌ No | ✅ Yes |
| MAC changes at router? | N/A | ✅ Yes — rewritten per hop |

---

## 🛠️ Tools Used

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) — Network simulation
- Simulation Mode — PDU capture and inspection
- ICMP ping — Traffic generation

---

## 📚 Skills Practiced

- Reading OSI Model and PDU Detail tabs in Packet Tracer
- Tracing Layer 2 and Layer 3 addressing across hops
- Understanding the role of the default gateway in routing
- Differentiating local vs. remote network communication behavior

---

## 🎓 Part of My Networking Journey

This lab is part of my hands-on networking practice as I work toward the **CCST Networking** certification through Cisco Skills for All.

Check out my other Packet Tracer labs:
- 🏠 Home Network Setup
- ⚙️ DHCP Server Configuration
- 📐 IPv4 Subnetting

---

*Built with Cisco Packet Tracer | Cisco NetAcad*
