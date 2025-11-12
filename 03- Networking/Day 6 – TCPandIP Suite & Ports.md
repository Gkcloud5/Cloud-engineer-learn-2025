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
* Before source and destination talk they will make 3 step handshake
* Step1: syn (synchronize)
	* Source --> Destination
	* Hey i like to connect now
	* Sends packet with SYN flag=1
* Step2: Syn-Ack
	* Destination --> Source
	* Okay, i am ready to connect
	* Sends packet with SYN=1, ACK=1
* Step3: ACK
	* Source --> destination
	* Got it, Lets start connection
	* Sends final ack
* Step4: FIN
	* When communication ends each side sends a FIN and ack to properly close the connection

### ICMP protocol:
* Helps to diagnose network issue
* what it does:
	* Checks if another device on the network reachable
	* Measure latency
	* Reports network error
