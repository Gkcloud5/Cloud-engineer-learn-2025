
### **Packet Forwarding Process (Step-by-Step)**

1. Router receives a packet.
2. Reads the **destination IP**.
3. Looks in its **routing table** for a matching route.
4. If found:
    - Forwards packet to the **next hop** router.    
5. If not found:
    - Sends it to the **default route (0.0.0.0/0)** — like “send to the Internet.”    
6. If no route at all:
    - Drops the packet ❌ (unreachable).

```
It's heart of how the internet works
```

### 5.1 why?
* Generally message will pass through many routers and networks to reach destination
* Router decides:
	* Which path is best to send data
	* How to move safely
	* Where deliver next

### 5.2 what is routing?
* Routing is process of finding best path in network
	* Router will help to do that work

### 5.3 What is packet?
* Small chunks of data
* It has
	* Actual data
	* Source IP address
	* Destination IP address

### 5.4 When we using routing?
* If destination is in different network

### 5.5 Workflow:
* Browser typed google.com
* Step1: DNS resoultion
	* DNS have mostly IP address o