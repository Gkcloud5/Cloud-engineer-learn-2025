
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
	1. 