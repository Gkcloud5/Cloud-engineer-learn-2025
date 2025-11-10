
![[Pasted image 20251109011908.png]]


* If multiple device connected on router there is a chance for data mixed up with other connections router
* to avoid we need rules:
	* identify who the message is
	* Ensure the message reaches correctly
	* Detect error during transmission

### What is data link later:
* It's layer 2 of OSI model
* It control how data is transfer for transmission and how access to the physical medium

### What is ethernet:
* How device identify each other -> using mac address
* How data is packaged into frames

### Complete workflow:
* Data comes from the network layer --> with IP packet
* Data link layer will wraps that packet into frames
	* Header -> Has source and destination MAC
	* payload -> The actual IP packet
	* Frame check sequence 
* MAC addressing:
	* Each NIC has unique MAC address
	* Check destination MAC on router
		* If match then send data to that destination
		* If not will check with ARP and find destination
* Converts packet to bits and sent over cable or air
* Before convert, it will correct sequence


 