# NETWORKING

The network infrastructure contains three categories of hardware components, as shown in the figure:

End devices
Intermediate devices
Network media

Some examples of end devices are as follows:

Computers (workstations, laptops, file servers, web servers)
Network printers
Telephones and teleconferencing equipment
Security cameras
Mobile devices (such as smart phones, tablets, PDAs, and wireless debit/credit card readers and barcode scanners)

TCP/IP MODEL

Application Layer

Responsible for end-user services like web browsing, email, and file transfers.
Examples: HTTP, FTP, SMTP, DNS, SSH.
Transport Layer

Ensures reliable data transfer and error handling.
Protocols: TCP (reliable, connection-oriented) and UDP (faster, connectionless).
Internet Layer

Manages addressing, routing, and packet forwarding.
Protocols: IP (addressing), ICMP (error reporting), ARP (address resolution).
Network Access Layer (Link Layer)

Handles physical hardware connections, such as Ethernet and Wi-Fi.
Defines how data is physically transmitted over the network.

+--------------------+--------------------+
|   Application     |   HTTP, FTP, SMTP   |
|       Layer       |   DNS, SSH, etc.    |
+--------------------+--------------------+
|   Transport       |   TCP, UDP          |
|       Layer       |   Flow Control, etc.|
+--------------------+--------------------+
|   Internet        |   IP, ICMP, ARP     |
|       Layer       |   Routing, etc.     |
+--------------------+--------------------+
|   Network         |   Ethernet, Wi-Fi   |
|   Access Layer    |   Physical Media    |
+--------------------+--------------------+

The two main models in computer network communication are:

OSI Model (Open Systems Interconnection Model)

Consists of 7 layers:
Physical Layer – Manages physical connections.
Data Link Layer – Handles error detection and MAC addresses.
Network Layer – Manages IP addressing and routing.
Transport Layer – Ensures end-to-end communication (TCP/UDP).
Session Layer – Manages sessions and connections.
Presentation Layer – Handles encryption and data format conversion.
Application Layer – Provides services like HTTP, FTP, and DNS.
The OSI model is a theoretical framework used for standardizing network communication.
TCP/IP Model (Transmission Control Protocol/Internet Protocol Model)

Consists of 4 layers:
Application Layer – Similar to OSI's top three layers (HTTP, FTP).
Transport Layer – Manages communication (TCP/UDP).
Internet Layer – Handles IP addressing and routing.
Network Access Layer – Manages physical connections and MAC addresses.
The TCP/IP model is the practical model used in the internet and modern networks.

OSI Model and TCP/IP Model Comparison
Because TCP/IP is the protocol suite in use for internet communications, why do we need to learn the OSI model as well?

The TCP/IP model is a method of visualizing the interactions of the various protocols that make up the TCP/IP protocol suite. It does not describe general functions that are necessary for all networking communications. It describes the networking functions specific to those protocols in use in the TCP/IP protocol suite. For example, at the network access layer, the TCP/IP protocol suite does not specify which protocols to use when transmitting over a physical medium, nor the method of encoding the signals for transmission. OSI Layers 1 and 2 discuss the necessary procedures to access the media and the physical means to send data over a network.

The protocols that make up the TCP/IP protocol suite can be described in terms of the OSI reference model. The functions that occur at the internet layer in the TCP/IP model are contained in the network layer of the OSI Model, as shown in the figure. The transport layer functionality is the same between both models. However, the network access layer and the application layer of the TCP/IP model are further divided in the OSI model to describe discrete functions that must occur at these layers.

The key similarities are in the transport and network layers; however, the two models differ in how they relate to the layers above and below each layer:

OSI Layer 3, the network layer, maps directly to the TCP/IP internet layer. This layer is used to describe protocols that address and route messages through an internetwork.
OSI Layer 4, the transport layer, maps directly to the TCP/IP transport layer. This layer describes general services and functions that provide ordered and reliable delivery of data between source and destination hosts.
The TCP/IP application layer includes several protocols that provide specific functionality to a variety of end user applications. The OSI model Layers 5, 6, and 7 are used as references for application software developers and vendors to produce applications that operate on networks.
Both the TCP/IP and OSI models are commonly used when referring to protocols at various layers. Because the OSI model separates the data link layer from the physical layer, it is commonly used when referring to these lower layers.


ETHERNET frame 

An Ethernet frame is the basic data unit in an Ethernet network. It encapsulates data for transmission over LAN (Local Area Network) and includes addressing and error-checking information to ensure reliable communication.

Main Components of an Ethernet Frame:
1.Preamble (7 bytes) & Start Frame Delimiter (1 byte)

Synchronizes communication between sender and receiver.

2.Destination MAC Address (6 bytes)

Identifies the receiver's MAC address.
3.Source MAC Address (6 bytes)

Identifies the sender's MAC address.
4.EtherType/Length (2 bytes)

Specifies the type of protocol (e.g., IPv4, IPv6, ARP) or 5.length of the frame.
5.Payload/Data (46–1500 bytes)

Contains actual data being transmitted (e.g., an IP packet).
6.Frame Check Sequence (FCS) (4 bytes)

Provides error detection using a CRC (Cyclic Redundancy Check).

+--------+------------+---------+----------+-----+
| Preamble | Header | Payload | FCS |
+--------+------------+---------+----------+-----+


ENCAPSULATION

Encapsulation in Networking
Encapsulation is the process of wrapping data with the necessary protocol information as it moves through the layers of the TCP/IP or OSI model. Each layer adds its own header (and sometimes a trailer) to ensure proper communication.

Encapsulation Process in TCP/IP Model
1️⃣ Application Layer:

Data is generated (e.g., an email, web request).
No headers yet, just raw data.
2️⃣ Transport Layer:

Adds a TCP/UDP header (Port numbers, sequencing, error checking).
The data is now called a Segment.
3️⃣ Internet Layer:

Adds an IP header (Source & Destination IP Addresses).
The segment becomes a Packet.
4️⃣ Network Access Layer (Data Link & Physical):

Adds a MAC header & FCS (Frame Check Sequence).
The packet is now called a Frame.
The frame is converted into Bits for transmission.

Decapsulation
The reverse process happens at the receiver's end, where each layer removes its header until only the original data remains.

Encapsulation (Sender Side)
Each layer adds its own header as data moves down the stack.

+---------------------------+   Application Layer
|         DATA              |   (Message)
+---------------------------+
|  TCP/UDP HEADER + DATA    |   Transport Layer (Segment)
+---------------------------+
|   IP HEADER + SEGMENT     |   Internet Layer (Packet)
+---------------------------+
| MAC HEADER + PACKET + FCS |   Network Access Layer (Frame)
+---------------------------+
|     0s and 1s (BITS)      |   Physical Layer (Transmission)
+---------------------------+

Decapsulation (Receiver Side)
The reverse happens as data moves up the stack.

+---------------------------+
|     0s and 1s (BITS)      |   Physical Layer (Received Bits)
+---------------------------+
| MAC HEADER + PACKET + FCS |   Network Access Layer (Frame)
+---------------------------+
|   IP HEADER + SEGMENT     |   Internet Layer (Packet)
+---------------------------+
|  TCP/UDP HEADER + DATA    |   Transport Layer (Segment)
+---------------------------+
|         DATA              |   Application Layer (Final Message)
+---------------------------+


OSI Model (7 Layers)       TCP/IP Model (4 Layers)
---------------------------------------------------
|  Application (Layer 7)  |  Application Layer    |
|  Presentation (Layer 6) |  (HTTP, FTP, SMTP)    |
|  Session (Layer 5)      |  -------------------- |
|  ---------------------- |  Transport Layer     |
|  Transport (Layer 4)    |  (TCP, UDP)          |
|  ---------------------- |  -------------------- |
|  Network (Layer 3)      |  Internet Layer      |
|  (IP, ICMP, ARP)        |  (IP, ICMP)          |
|  ---------------------- |  -------------------- |
|  Data Link (Layer 2)    |  Network Access      |
|  Physical (Layer 1)     |  (Ethernet, Wi-Fi)   |
---------------------------------------------------
IPv4 UniCast

IPv4 unicast is a type of network communication where data is sent from one sender (source) to one specific recipient (destination). It is the most common method used in networking for one-to-one communication.

IPV4 Broadcast

IPv4 broadcast is a type of network communication where a packet is sent from one sender to all devices in the network. It is used when a device needs to send data to every host in a local network segment.

Key Characteristics of IPv4 Broadcast:
✅ One-to-All Communication – The packet is sent to all devices in the same network.
✅ Uses a Special Broadcast Address – The destination IP address is set to 255.255.255.255 (limited broadcast) or the network’s broadcast address.
✅ No Routing Across Networks – Broadcasts do not pass through routers unless special configurations are made.
✅ Used for Network Discovery and Protocols – Commonly used by ARP (Address Resolution Protocol), DHCP, and other protocols.

IPV4 Multicast

IPv4 multicast is a type of network communication where data is sent from one sender to multiple specific receivers who have joined a multicast group. This is different from unicast (one-to-one) and broadcast (one-to-all).

Key Characteristics of IPv4 Multicast:
✅ One-to-Many Communication – Packets are sent to multiple devices, but only those that have subscribed to the multicast group receive them.
✅ Uses Special Multicast IP Addresses – 224.0.0.0 – 239.255.255.255 (Class D IP range).
✅ Efficient Bandwidth Usage – The sender sends one copy of the data, and routers distribute it only to devices that need it.
✅ Requires Multicast Group Subscription – Devices must subscribe to a multicast group using IGMP (Internet Group Management Protocol).

TYPES OF IPV4 Addresses

Types of IPv4 Addresses
IPv4 addresses are categorized into different types based on their function and scope. These include:

1️⃣ Unicast Addresses (One-to-One Communication)
📌 Definition: Used to send data from one device to another specific device on a network.
📌 Example: When you visit a website, your computer sends requests to the server’s unicast IP address.
📌 Address Ranges:

Public IPs: Assigned by ISPs, used on the Internet (e.g., 8.8.8.8).
Private IPs: Used in local networks (LANs). Not routable on the Internet.
Class A: 10.0.0.0 – 10.255.255.255
Class B: 172.16.0.0 – 172.31.255.255
Class C: 192.168.0.0 – 192.168.255.255
Loopback (127.0.0.1): Used for testing within a device.
2️⃣ Broadcast Addresses (One-to-All Communication)
📌 Definition: Used to send data to all devices in a network segment.
📌 Types:

Limited Broadcast (255.255.255.255) – Sent to all devices in the same local network, not forwarded by routers.
Directed Broadcast (<Network ID>.255) – Sent to all devices in a specific subnet (e.g., 192.168.1.255).
📌 Example: Used by ARP, DHCP Discover, and Wake-on-LAN.
3️⃣ Multicast Addresses (One-to-Many Communication)
📌 Definition: Used to send data to multiple specific devices that have subscribed to a multicast group.
📌 Address Range: 224.0.0.0 – 239.255.255.255 (Class D).
📌 Examples:

224.0.0.5 – OSPF (Routing Protocol)
239.1.1.1 – IPTV Streaming
4️⃣ Anycast Addresses (One-to-Nearest Communication)
📌 Definition: Used to route data to the nearest device (in terms of network topology) with a specific IP address.
📌 Used in:

CDNs (Content Delivery Networks) (e.g., Cloudflare, Google DNS 8.8.8.8).
IPv6 routing (widely used in IPv6 but less common in IPv4).

DYNAMIC ADRESSING USING DHCP

Dynamic Host Configuration Protocol (DHCP) is a network protocol that automatically assigns IP addresses and other network configurations (subnet mask, gateway, DNS) to devices on a network. This eliminates the need for manual IP address configuration.

 DHCP Dynamic IP Assignment Process

    [ Client (PC) ]      [ DHCP Server ]
         │                      │
  1️⃣  ───►  DHCP Discover  ───►  (Broadcast: "I need an IP!")
         │                      │
  2️⃣  ◄───  DHCP Offer  ◄───  ("You can use 192.168.1.100")
         │                      │
  3️⃣  ───►  DHCP Request  ───►  ("I accept 192.168.1.100")
         │                      │
  4️⃣  ◄───  DHCP ACK  ◄───  ("Confirmed! Use 192.168.1.100 for 8 hours")
         │                      │

1️⃣ DHCP Discover → Client requests an IP address (broadcast).
2️⃣ DHCP Offer → DHCP server responds with an available IP.
3️⃣ DHCP Request → Client accepts the IP.
4️⃣ DHCP Acknowledgment (ACK) → Server confirms assignment and lease

GATEWAYS TO OTHER Networks


The router provides a gateway through which hosts on one network can communicate with hosts on different networks. Each interface on a router is connected to a separate network.

The IPv4 address assigned to the interface identifies which local network is connected directly to it.

Every host on a network must use the router as a gateway to other networks. Therefore, each host must know the IPv4 address of the router interface connected to the network where the host is attached. This address is known as the default gateway address. It can be either statically configured on the host or received dynamically by DHCP.

When a wireless router is configured to be a DHCP server for the local network, it automatically sends the correct interface IPv4 address to the hosts as the default gateway address. In this manner, all hosts on the network can use that IPv4 address to forward messages to hosts located at the ISP and get access to hosts on the internet. Wireless routers are usually set to be DHCP servers by default.

The IPv4 address of that local router interface becomes the default gateway address for the host configuration. The default gateway is provided, either statically or by DHCP.

When a wireless router is configured as a DHCP server, it provides its own internal IPv4 address as the default gateway to DHCP clients. It also provides them with their respective IPv4 address and subnet mask, as shown in the figure.



 # Introduction to NAT

 Network Address Translation (NAT) is a process where a router modifies IP addresses in network packets as they pass through. NAT enables multiple devices in a private network to share a single public IP address for Internet access.

  How NAT Works
1️⃣ A device in a private network (e.g., 192.168.1.10) wants to access the internet.
2️⃣ The router with NAT replaces the private IP with its public IP before sending the request to the internet.
3️⃣ When the response from the internet arrives, the router translates the public IP back to the private IP and forwards it to the correct device.

#  NAT (Network Address Translation) in Action

        [ Private Network ]                [ Public Internet ]
  ┌──────────────────────────┐        ┌──────────────────────────┐
  │ PC1: 192.168.1.10        │        │                          │
  │ PC2: 192.168.1.11        │        │       Web Server         │
  │ PC3: 192.168.1.12        │        │      203.0.113.50        │
  └──────────┬───────────────┘        └──────────▲───────────────┘
             │                                  │
       ┌────▼────────────────┐          ┌──────┴──────┐
       │  NAT Router          │          │ Internet   │
       │ Public IP: 203.0.113.5 │          └──────────┘
       └───────────────────────┘

1️⃣ PC1 (192.168.1.10) requests a web page from 203.0.113.50.
2️⃣ NAT translates the private IP to the router’s public IP (203.0.113.5) and sends the request.
3️⃣ The web server responds to 203.0.113.5.
4️⃣ NAT translates it back to 192.168.1.10 and delivers the response to PC1.

#  Address Resolution Protocol (ARP) Process

ARP (Address Resolution Protocol) is used to map an IPv4 address to a MAC (Media Access Control) address within a local network (LAN). It helps devices communicate over Ethernet by finding the hardware address (MAC) associated with an IP address.

 # How ARP Works (Step-by-Step)
💡 Imagine PC1 (192.168.1.10) wants to send data to PC2 (192.168.1.20) on the same network but doesn’t know its MAC address.

Step 1: PC1 Sends an ARP Request (Broadcast)
📌 PC1 broadcasts an ARP Request to all devices on the LAN:
📢 “Who has 192.168.1.20? Tell me your MAC address!”
✔ Destination MAC: FF:FF:FF:FF:FF:FF (Broadcast MAC)
✔ Source MAC: PC1’s MAC
✔ Target IP: 192.168.1.20

 Step 2: PC2 Sends an ARP Reply (Unicast)
📌 PC2 receives the ARP request (because it matches its IP).
📌 PC2 sends an ARP Reply directly to PC1 (Unicast):
✔ “I am 192.168.1.20, my MAC address is AA:BB:CC:DD:EE:FF.”

Step 3: PC1 Updates Its ARP Table
📌 PC1 stores PC2’s MAC address in its ARP cache for future communication.
📌 Now, PC1 can send data to PC2 using Layer 2 (MAC) addresses.

# CREATING A LAN NETWORK USING PACKET TRACER ACTIVITY.

 Steps to Create a LAN in Packet Tracer
1️⃣ Open Cisco Packet Tracer
Launch Cisco Packet Tracer on your computer.
2️⃣ Add Networking Devices
Select Devices from the bottom panel:
Switch (e.g., 2960 switch)
PCs or Laptops (End devices)
3️⃣ Connect the Devices
Use cables to connect:
PCs to the switch using Copper Straight-Through cables.
Click a PC ➝ Click the FastEthernet0 port ➝ Click the Switch ➝ Select an available FastEthernet port.
4️⃣ Assign IP Addresses
Click on each PC ➝ Go to Desktop ➝ Click IP Configuration.
Assign static IP addresses (for example):
PC1: 192.168.1.2 / Subnet: 255.255.255.0
PC2: 192.168.1.3 / Subnet: 255.255.255.0
5️⃣ Test Connectivity
Open Command Prompt in one PC (Desktop > Command Prompt).
Use the ping command

Basic LAN Network Diagram

  [PC1] ----|
            |----[Switch]----[PC3]
  [PC2] ----|


# Common TCP and UDP Port Numbers

Ports are categorized into well-known ports (0-1023), registered ports (1024-49151), and dynamic/private ports (49152-65535). Below are some of the most commonly used TCP and UDP ports:

1. Well-Known Ports (0-1023)
   
Port Protocol	Description
20	TCP	FTP (Data Transfer)
21	TCP	FTP (Control)
22	TCP	SSH (Secure Shell)
23	TCP	Telnet (Unsecure Remote Login)
25	TCP	SMTP (Simple Mail Transfer Protocol)
53	TCP/UDP	DNS (Domain Name System)
67	UDP	DHCP (Server)
68	UDP	DHCP (Client)
69	UDP	TFTP (Trivial File Transfer Protocol)
80	TCP	HTTP (Web Traffic)
88	TCP/UDP	Kerberos Authentication
110	TCP	POP3 (Post Office Protocol v3)
119	TCP	NNTP (Network News Transfer Protocol)
123	UDP	NTP (Network Time Protocol)
137-139	TCP/UDP	NetBIOS (Name, Datagram, and Session Services)
143	TCP	IMAP (Internet Message Access Protocol)
161-162	UDP	SNMP (Simple Network Management Protocol)
179	TCP	BGP (Border Gateway Protocol)
389	TCP/UDP	LDAP (Lightweight Directory Access Protocol)
443	TCP	HTTPS (Secure Web Traffic)
465	TCP	SMTPS (Secure SMTP)
514	UDP	Syslog
636	TCP/UDP	LDAPS (Secure LDAP)
993	TCP	IMAPS (Secure IMAP)
995	TCP	POP3S (Secure POP3)


1. Registered Ports (1024-49151)
   
Port Number	Protocol	Description
1433-1434	TCP/UDP	Microsoft SQL Server
1521	TCP	Oracle Database
3306	TCP	MySQL Database
3389	TCP	RDP (Remote Desktop Protocol)
5060-5061	TCP/UDP	SIP (Session Initiation Protocol)
5900-5901	TCP	VNC (Virtual Network Computing)
8080	TCP	HTTP Alternative Port


3. Dynamic/Private Ports (49152-65535)
   
These are temporary ports assigned for client-side communications in applications such as web browsing, VoIP, and online gaming.
Examples:
49152-65535: Ephemeral ports used dynamically by applications like Skype, Zoom, and web services.

 # Socket Pairs
The source and destination ports are placed within the segment. The segments are then encapsulated within an IP packet. The IP packet contains the IP address of the source and destination. The combination of the source IP address and source port number, or the destination IP address and destination port number is known as a socket.

In the example in the figure, the PC is simultaneously requesting FTP and web services from the destination server.

# Netstat Command 

Unexplained TCP connections can pose a major security threat. They can indicate that something or someone is connected to the local host. Sometimes it is necessary to know which active TCP connections are open and running on a networked host. Netstat is an important network utility that can be used to verify those connections. As shown below, enter the command netstat to list the protocols in use, the local address and port numbers, the foreign address and port numbers, and the connection state.

Basic netstat Commands
Command	Description

1.netstat	Shows all active connections (both incoming and outgoing).
2.netstat -a	Displays all active and listening ports.
3.netstat -n	Shows IP addresses and port numbers instead of resolving hostnames.
4.netstat -p <protocol>	Filters results for a specific protocol (TCP/UDP). Example: netstat -p tcp
5.netstat -r	Displays the routing table (similar to route command).
6.netstat -i	Shows network interfaces and statistics (Linux/macOS).
7.netstat -s	Displays summary statistics for each protocol (TCP, UDP, ICMP, etc.).

# URI, URN, and URL
Web resources and web services such as RESTful APIs are identified using a Uniform Resource Identifier (URI). A URI is a string of characters that identifies a specific network resource. As shown in the figure, a URI has two specializations:

Uniform Resource Name (URN) - This identifies only the namespace of the resource (web page, document, image, etc.) without reference to the protocol.
Uniform Resource Locator (URL) - This defines the network location of a specific resource on the network. HTTP or HTTPS URLs are typically used with web browsers. Other protocols such as FTP, SFTP, SSH, and others can be used as a URL. A URL using SFTP might look like: sftp://sftp.example.com.
These are the parts of a URI, as shown in the figure:

Protocol/scheme - HTTPS or other protocols such as FTP, SFTP, mailto, and NNTP
Hostname - w​ww.example.com
Path and file name - /author/book.html
Fragment - #page155

# NETWORK APPLICATION Services

Examples of Network Application Services in Use
Web Browsing → Uses HTTP/HTTPS (Google Chrome, Firefox)
Email Communication → Uses SMTP/IMAP/POP3 (Gmail, Outlook)
File Sharing → Uses FTP/SFTP (Google Drive, Dropbox)
Remote Desktop → Uses RDP/SSH/Telnet (Microsoft Remote Desktop, PuTTY)
DNS Resolution → Converts google.com to an IP address via DNS
VoIP Calling → Uses SIP/RTP (Zoom, WhatsApp Calls)

# Syntax Checker - The nslookup Command
When you manually configure a device for network connectivity, recall that you also include a DNS server address. For home networks, this configuration is typically handled by DHCP running on the home router. Your ISP provides the DNS server address to your home router, and then your home router uses DHCP to send the configuration to all the devices connected to its network. When you type the name for a website, such as www.cisco.com, the DNS client running on your device first asks the DNS server for the IP address, such as 172.230.155.162, before sending out your HTTP request.

You can use the command nslookup to discover the IP addresses for any domain name. In this Syntax Checker activity, practice entering the nslookup command in both Windows and Linux.

# Overview of Troubleshooting Commands
A number of software utility programs are available that can help identify network problems. Most of these utilities are provided by the operating system as command line interface (CLI) commands. The syntax for the commands may vary between operating systems.

Some of the available utilities include:

ipconfig - Displays IP configuration information.
ping - Tests connections to other IP hosts.
netstat - Displays network connections.
tracert - Displays the route taken to the destination.
nslookup - Directly queries the name server for information on a destination domain.

# The ipconfig Command

When a device does not get an IP address, or has an incorrect IP configuration, it cannot communicate on the network or access the internet. On Windows devices, you can view the IP configuration information with the ipconfig command at the command prompt. The ipconfig command has several options that are helpful including /all, /release, and /renew.

# PING COMMAND

The ping command is used to test network connectivity between two devices by sending ICMP (Internet Control Message Protocol) Echo Request packets and measuring response times.

# Basic Syntax

ping [options] destination

destination: Can be an IP address (e.g., 8.8.8.8) or a domain name (e.g., google.com).

# Basic Ping Test

ping google.com

Sends packets to google.com and waits for a response.
Helps check if a host is reachable.

When a ping is sent to an IP address, a packet known as an echo request is sent across the network to the IP address specified. If the destination host receives the echo request, it responds with a packet known as an echo reply. If the source receives the echo reply, connectivity is verified by the reply from the specific IP address. The ping is not successful if a message such as request timed out or general failure appears.

If a ping command is sent to a name, such as ww​w.cisco.com, a packet is first sent to a DNS server to resolve the name to an IP address. After the IP address is obtained, the echo request is forwarded to the IP address and the process proceeds. If a ping to the IP address succeeds, but a ping to the name does not, there is most likely a problem with DNS.

 # Ping Results
If ping commands to both the name and IP address are successful, but the user is still unable to access the application, then the problem most likely resides in the application on the destination host. For example, it may be that the requested service is not running.

If neither ping is successful, then network connectivity along the path to the destination is most likely the problem. If this occurs, it is common practice to ping the default gateway. If the ping to the default gateway is successful, the problem is not local. If the ping to the default gateway fails, the problem resides on the local network.

In some cases, the ping may fail but network connectivity is not the problem. A ping may fail due to the firewall on the sending or receiving device, or a router along the path that is blocking the pings.

The basic ping command usually issues four echoes and waits for the replies to each one. It can, however, be modified to increase its usefulness. The options listed in the figure display additional features available.

# SUMMARY OF NETWORK TESTING utilities

Command	Function
tracert (A)	Displays the route taken to the destination.
ping (B)	Tests connections to other IP hosts.
netstat (C)	Displays network connections.
nslookup (D)	Directly queries the name server for information on a destination domain.
ipconfig (E)	Displays IP configuration information.