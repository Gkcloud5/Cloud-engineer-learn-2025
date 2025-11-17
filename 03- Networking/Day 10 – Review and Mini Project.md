
### 10.1 End to End data flow:
1. User input: google.com
2. DNS resolution: Finding IP
	1. First check local cache, OS cache and then router cache
	2. If not found then will check with DNS servers 8.8.8.8
	3. IP founded after used DNS
	4. Now browser knows the IP address of domain, where to send data
3. TCP connection: 3-way handshake
	1. Syn -- Pc to destination server --> "is okay to connect?"
	2. Ack-Syn -- Destination server to PC --> I'm Ready to connect
	3. Ack -- PC to destination --> We can share file now
	4. Fin -- Once data transfer is completed, we can close the connection now
4. SSL/TLS handshake
	1. Before data exchange
		1. Browser request secure connection
		2. Server sends its SSL certificate
		3. Browser verifies authenticity
		4. Both accept session key encryption
5. HTTP request:
	1. GET data from server
6. Router and NAT:
	1. Request from browser to router
	2. Router forwards packets to ISP
7. ISP routing:
	1. By using routing table packet will send diff routes and reach final.
8. Server Processing:
	1. Load balance receive packet and pick nearby health server
	2. Server sends back HTTP response
9. Packet return
	1. Google server --> ISP --> My router
	2. Router use NAT to find which device in network requested and send data to that device
10. Display output in screen