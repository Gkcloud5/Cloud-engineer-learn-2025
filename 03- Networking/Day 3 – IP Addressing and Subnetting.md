```

           🌐 IP Addressing Overview (80/20)
─────────────────────────────────────────────
📦 IPv4 Structure
 - 32-bit, 4 octets
 - Network + Host

🏷️ Classes
 - A: 1–126 (/8)
 - B: 128–191 (/16)
 - C: 192–223 (/24)

🧮 Subnet & CIDR
 - Mask: 255.255.255.0 = /24
 - Defines network boundary

🏠 Private vs Public
 - Private: 10.x.x.x, 172.16.x.x, 192.168.x.x
 - Public: Internet-visible
 - NAT bridges them

🔢 IPv6
 - 128-bit, hex format
 - Huge space, no NAT

🔁 Loopback & Reserved
 - 127.0.0.1 = self-test
 - 0.0.0.0 = any
 - 255.255.255.255 = broadcast
─────────────────────────────────────────────

```


### Why:
* Every device on a network has unique identity to send and receive data
	* That identity is IP address in network
* To assign IP address in network we need to use subnet to accomplish it

### Assigning an IP address:
* Static IP
* Dynamic IP

### IP address structure:
* Network ID and Host ID
	* Host ID is count like how many IP we can use in that network

### Subnet mask:
* It's divider
* It defines how much of the IP address is belongs to the network and how much to the host
* 255.255.255.0
	* 3 network and 1 host
		* In that host it has 1-254 IP address
		* Total usable IP is 254

### IPv4 classes:
* A --> 1 to 126 ranges -> 255.0.0.0 --> very large
* B --> 128 to 191 range --> 255.255.0.0 --> /16
* C --> 192 to 223 range --> 255.255.255.0 --> /24 range

### CIDR:
* /n --> n - Represents how many host belongs to the network
* /27 --> 11111111.11111111.11111111.11100000 --> 128+