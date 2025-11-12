![[ChatGPT Image Nov 12, 2025, 12_45_33 AM.png]]


* How data move between networks --> routing
* How data is actually communicated and managed inside the connection


### 6.1 why?
* Even we find route we need to make sure data is sent and recieve without any issue 
* we need to make sure following things
	* Establish connection
	* Guarantee delivery
	* Control data flow
	* Identify which app data belongs like browser, email, ..
* The above all resolved by using TCP/IP
* It defines how communication happens between computer over the network

### 6.2 About TCP/IP suite:
* It's foundation of the internet
* It's comes under transport layer

### 6.3 TCP vs UDP?
* Both sit on top of IP
* They help deliver the data from one computer to another

### 6.4 TCP protocol:
* Transmission Control Protocol
* Reliable, ordered, connection oriented communication
* Features:
	* Establish connection before send
	* retransmit lost packets
	* Packet arrive in correct sequence
	* flow control

### 6.5 UDP protocol:
* Fast, connection less communication

### 6.6 TCP 3 way handshake:
* 