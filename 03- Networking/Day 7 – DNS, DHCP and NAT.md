
![[ChatGPT Image Nov 12, 2025, 11_26_58 PM.png]]

```
Services that automate network operations and make internet usable for everyone
```

### 7.1 Why?
* Generally we type domain name in browser
	* DNS will help to find a IP address of domain
		* In order to reach destination we need only IP address
* DHCP --> Automatically assign IP address to device when it's connected in network
* NAT --> Due to shortage of IPv4. NAT is very useful why because for an router only need one public address to connect internet, the devices that are connected to routed all are have NAT IP address to identify what IP sent what data.

### 7.2 DNS?
* Domain name system
* It's phonebook of internet
* It translates domain name into IP address
* Process: (When type domain in browser)
	* 1. cache check: Cache check to know the IP address
	* 2. OS cache check: Check local DNS to know the IP address
	* 3.Router/ISP: Devices asks configured DNS server
	* 4. Recursive query begins:
		* DNS servers start query
		* 1. Root DNS --> "Where .com servers"
		* 2.TLS --> "Where is google.com DNS"
		* 3.Authoritative --> "Here is IP 196.^^.^^^.
	* 5. Response returned:
		* DNS server cache the answer and sends it back to your computer
	* 6. Browser connect to IP:
		* Now browser can directly connected to IP

### 7.3 DHCP:
* Dynamic host configuration protocol
* DHCP automatically gives IP address and network setting to decide when they connect to network
* **DORA** Process:
	* Discover --> checking any DHCP is running or not
	* Offer --> Server to client --> I have a IP for you
	* Request --> Client to Server --> Yes, i am okay to use the IP
	* Ack --> Server to client --> Done, IP assigned


### 7.4 NAT: Network address translation:
* NAT allows multiple devices in a private network to share a single public IP address to access network