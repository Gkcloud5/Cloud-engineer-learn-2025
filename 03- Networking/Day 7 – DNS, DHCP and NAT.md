
![[ChatGPT Image Nov 12, 2025, 11_26_58 PM.png]]

```
Services that automate network operations and make internet usable for everyone
```

### 7.1 Why?
* Generally we type domain name in browser
	* DNS will help to find a IP address of domain
		* In order to reach destination we need only IP address
* DHCP --> Automatically assign IP address to device when it's connected in network
* NAT --> Due to shortage of IPv4. nat is very useful why becuase for an router only need one public address to connect internet, the devices that are connected to routed all are have NAT IP address to identify what IP sent what data.

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
		* 3.Authoritative --> "Here is IP 196.