
# 🧠 10-Day Computer Networking Study Plan (80/20 + Interview Focused)

> 🎯 Goal: Master 20% of networking topics that cover 80% of real-world and interview questions.  
> 🕐 Duration: 10 Days (3–4 hours/day)  
> 💪 Focus: Learn → Visualize → Apply → Practice Interview Answers  

---

## 📅 [[Day 1 – Networking Fundamentals]] (Interview Foundation)
**🎯 Focus:** Understand how computers communicate.

### 📘 Topics
- [x] What is a computer network? (LAN, WAN, MAN, PAN)
- [ ] Difference between Router, Switch, and Hub
- [ ] Client-Server vs Peer-to-Peer models
- [ ] Types of network topologies

### 💡 Interview Focus
- What is a computer network?
- Difference between hub, switch, and router?
- Which topology is most reliable and why?

### ⚙️ Practice
- [ ] Draw your home/work network.
- [ ] Explain your drawing aloud in simple terms.

### 💬 Reflection
> How confident am I in explaining the difference between a router and a switch?

---

## 📅 Day 2 – OSI & TCP/IP Models
**🎯 Focus:** Learn how data communication happens layer by layer.

### 📘 Topics
- [ ] OSI 7 Layers and their functions
- [ ] TCP/IP 4-Layer model
- [ ] Data encapsulation and decapsulation
- [ ] Example protocols at each layer

### 💡 Interview Focus
- Explain the OSI model and its 7 layers.
- At which layer do routers and switches work?
- OSI vs TCP/IP model — differences?

### ⚙️ Practice
- [ ] Create a table mapping each OSI layer → example protocols → devices.

### 💬 Reflection
> Can I confidently explain each layer’s function in one sentence?

---

## 📅 Day 3 – IP Addressing & Subnetting
**🎯 Focus:** Understand how devices are identified in a network.

### 📘 Topics
- [ ] IPv4 structure and classes
- [ ] Subnet mask and CIDR notation
- [ ] Private vs Public IP
- [ ] IPv6 overview
- [ ] Loopback and reserved addresses

### 💡 Interview Focus
- What is a subnet mask?
- Difference between public and private IP?
- How many hosts can fit in /26 subnet?

### ⚙️ Practice
- [ ] Solve 3 subnetting examples.
- [ ] Assign IPs to 3 virtual devices and test `ping`.

### 💬 Reflection
> Do I understand how IPs are divided into networks and hosts?

---

## 📅 Day 4 – Data Link Layer & Ethernet
**🎯 Focus:** Learn how data moves within a local area network (LAN).

### 📘 Topics
- [ ] MAC Address
- [ ] ARP (Address Resolution Protocol)
- [ ] Ethernet frame format
- [ ] Switch operation (MAC table)

### 💡 Interview Focus
- What is the difference between MAC and IP addresses?
- How does ARP work?
- How does a switch forward frames?

### ⚙️ Practice
- [ ] Run `arp -a` in terminal.
- [ ] Capture ARP packets using Wireshark.

### 💬 Reflection
> Can I describe how a switch forwards packets inside a LAN?

---

## 📅 Day 5 – Routing & Packet Flow
**🎯 Focus:** Understand how data travels between networks.

### 📘 Topics
- [ ] Static vs Dynamic Routing
- [ ] Default gateway
- [ ] Packet forwarding and routing tables
- [ ] Packet journey: PC → Router → Internet

### 💡 Interview Focus
- What is a default gateway?
- How is routing different from switching?
- What happens when you type `google.com` in a browser?

### ⚙️ Practice
- [ ] Use `traceroute` or `tracert` to visualize hop-by-hop travel.

### 💬 Reflection
> Can I clearly explain how a packet finds its destination?

---

## 📅 Day 6 – TCP/IP Suite & Ports
**🎯 Focus:** Core Internet communication protocols.

### 📘 Topics
- [ ] TCP vs UDP
- [ ] 3-way handshake
- [ ] ICMP (ping)
- [ ] Common ports: HTTP(80), HTTPS(443), DNS(53), SSH(22)

### 💡 Interview Focus
- Difference between TCP and UDP?
- Explain 3-way handshake.
- Which ports are used for HTTP, HTTPS, DNS, SSH?

### ⚙️ Practice
- [ ] Use `netstat -an` or `ss` to see open connections.
- [ ] Capture TCP handshake in Wireshark.

### 💬 Reflection
> Can I describe TCP and UDP behavior with real examples?

---

## 📅 Day 7 – DNS, DHCP & NAT
**🎯 Focus:** Understand the services that automate network operations.

### 📘 Topics
- [ ] DNS resolution process
- [ ] DHCP lease process
- [ ] NAT types (Static, Dynamic, PAT)
- [ ] IP translation and Internet access

### 💡 Interview Focus
- How does DNS work?
- DHCP vs Static IP?
- What is NAT and why do we use it?

### ⚙️ Practice
- [ ] Run `nslookup google.com`
- [ ] Check your DHCP-assigned IP using `ipconfig /all`

### 💬 Reflection
> Can I explain how DNS converts a domain name into an IP address?

---

## 📅 Day 8 – Network Security & Firewalls
**🎯 Focus:** Learn how to protect and secure network communication.

### 📘 Topics
- [ ] Firewalls (hardware/software)
- [ ] Packet filtering and access control
- [ ] VPN basics (tunneling, encryption)
- [ ] HTTPS, SSH, SSL/TLS protocols

### 💡 Interview Focus
- What is a firewall and how does it work?
- What’s the difference between HTTP and HTTPS?
- How does a VPN secure communication?

### ⚙️ Practice
- [ ] View or edit firewall rules on your OS.
- [ ] Try allowing/denying specific ports.

### 💬 Reflection
> Can I describe how encryption and firewalls protect data?

---

## 📅 Day 9 – Wireless & Troubleshooting
**🎯 Focus:** Practical wireless networking and real-world problem-solving.

### 📘 Topics
- [ ] Wi-Fi basics (SSID, channel, frequency)
- [ ] Common tools: `ping`, `traceroute`, `nslookup`
- [ ] Network troubleshooting steps

### 💡 Interview Focus
- How do you troubleshoot no Internet access?
- What’s the difference between `ping` and `traceroute`?
- How to find and fix packet loss?

### ⚙️ Practice
- [ ] Simulate a disconnected network and fix it.
- [ ] Diagnose a ping failure using commands.

### 💬 Reflection
> Am I comfortable describing troubleshooting steps in sequence?

---

## 📅 Day 10 – Review & Mini Project (Final Interview Prep)
**🎯 Focus:** Combine everything and prepare for interviews.

### 📘 Topics
- [ ] End-to-end data flow: Browser → DNS → TCP/IP → Router → Server
- [ ] Real-world small network setup (LAN + Router + DHCP)
- [ ] Review top 30 interview questions

### 💡 Interview Focus
- What happens when you type `google.com` in a browser? *(Explain step-by-step)*
- How would you design a small office/home network?
- What’s your approach to diagnosing network failures?

### ⚙️ Practice
- [ ] Create a mini LAN in Cisco Packet Tracer.
- [ ] Test ping and DNS.
- [ ] Document the setup and results.

### 💬 Reflection
> Can I confidently explain networking concepts in interview scenarios?

---

## 🧾 Summary Table

| Day | Focus Area | Interview Keywords |
|------|-------------|--------------------|
| 1 | Networking Basics | Devices, Topologies, Models |
| 2 | OSI & TCP/IP | Layers, Protocols |
| 3 | IP Addressing | Subnetting, CIDR, IPv4 |
| 4 | Data Link | MAC, ARP, Ethernet |
| 5 | Routing | Gateway, Packet Flow |
| 6 | TCP/IP Suite | TCP/UDP, Ports |
| 7 | DNS/DHCP/NAT | IP Assignment, Name Resolution |
| 8 | Security | Firewalls, VPN, HTTPS |
| 9 | Wireless | Tools, Troubleshooting |
| 10 | Review | End-to-End Flow, Project |

---

## 🧩 Bonus: Top 10 Interview Questions

1. Explain the OSI model with examples.  
2. What’s the difference between a router, switch, and hub?  
3. What happens when you type `google.com` in a browser?  
4. How does DNS work?  
5. Explain the TCP 3-way handshake.  
6. Difference between TCP and UDP.  
7. What is ARP?  
8. What is subnetting and why is it important?  
9. How does NAT work?  
10. How do you troubleshoot Internet connection issues?

---

## 🧠 Final Notes

✅ Focus on **concept clarity**, not memorization.  
✅ Visualize **packet flow** in every concept.  
✅ After each day, **explain topics aloud** — interviews test communication clarity.  
✅ Use **Wireshark** and **Packet Tracer** to make theory real.

---

> 💬 “If you can explain how data moves from your computer to Google’s server in simple words — you’re ready for 90% of networking interviews.”  
