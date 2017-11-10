# FIT1047-Intro-Computer-System-and-Security-Revision



Network components
Client: 
provide access to internet users.

Server:
provides application and business logic, data storage, data access for the end users.

Switch:
Connect computers in a LAN (local area networks).

Router:
Connect two or more networks.

Internet
Internet is the network of networks. It connects millions networks and billions devices together. It is implemented using five network layers where each network layer communicates with one layer directly above or below with well-defined interfaces (sounds like a typical software-engineering job!).

Network Layers of Abstraction, and what each layer does (Internet Model). 
Application:
What messages are communicated between endpoints - client and server.

Transport:
Break messages into packets, make sure they arrive (logistician).

Networking:
Where should the packets go (how to travel from origin to destination).

Data link:
The link between this computer to next computer.

Physical:
Wifi, ADSL, network cables

Message Encapsulation in each network layer (Protocol data unit PDU)
Application: message
Transport: segement
Network: packet
Data link: frame
Physical: bit



Networks application layer architectures/workloads
Presentation logic:
User interface. How user controls application.

Application/business logic:
Rules certain application operates under, business-dependent.

Data access logic:
Data request and response rules between client and server.

Data storage:
Storage space for application program, data.

How work is splited between server and client (advantages / disdvantages)
Server-based architecture:
client: 
server: presentation, application, data access, data storage. 
disadvantages: server acts as a dumb terminal. It processes everything (billions/trillions requests) hence upgrade is expensive.
examples: 1960s Unix terminal. ssh

Client-based architecture:
client: presentation, application, data access.
server: data storage.
disadvangtages: data is transmitted back and forth between client and server. Creates network bottleneck/loads.
examples: late 1980s windows word file sharing

Client-Server architecture:
client: presentation, application.
server: data access, storage.
advangtages: balanced loads between client and server.
examples: 1990s WWW, Email.

Thin-Client architecture:
client: presentation.
server: application, data access, storage.
advangtages: server does complex computation for client.
examples: Gmail email classification.

Multi-Tier architecture:
client: presentation.
server-1: application.
server-2: data access.
...
server-i: storage.
...
server-n
advangtages: distribute network loads evenly. We can only upgrade servers with high traffics.
disadvangtages: high internal network loads between servers. Difficult to test.    

Peer-To-Peer architecture:
client: presentation, application, data access, data storage. 
server: presentation, application, data access, data storage. 
examples: file sharing, Skype, 8bITProject multi-player.



Network Physical and Data Link Layers
Basic LAN (local area network) components:
client, server, network interface card (NIC), switch.

What physical layer does:
convert sequence of bits into signals and back.

How does information transmit:
physical signals.

List three types of physical signals:
- electronic signals. For example, through cooper wire, cable.
- radio wave. Through air, space.
- light wave. Through space, optic fiber.

Digital transmission (transmitted data represented in either 0 or 1s)
Bipolar signals:
Signals that change between negative to positve polarity/voltage.

NRZ: 
non-return-to-zero encoding. A 0 represents negative polarity/voltage, and a 1 represents positive polarity/voltage.

NRZI:
non-return-to-zero-inverted encoding. A 0 represents no change in polarity/voltage, and a 1 represents a change in polarity/voltage.

Manchester encoding:
The change between negative and positive polarity/voltage occurs between the middle of a transmitting bit. A 0 represents a negative to positive polarity change, and a 1 represents a positive to negative polarity change.

Analog transmission (transmitted data represented in continuous values)
Frequency modulation:
corresponds to pitch of sound wave. How many cycles per second.

Amplitude modulation:
corresponds to loudness of sound wave. 

Phase modulation:
the initial angle at which the sound wave begins.

What data link layer does:
- encode/decode between frames and signals.
- control access to physical layer (Media Access Control MAC).
- error detection.
- interface with network layer.

Contention-based MAC (play by rules)
Any device can transmit at any time:
first-come-first-serve basis.

Collions - two devices tramsmitting at the same time:
avoid collision by carrier sensing (listen on the network for transmission).

Ethernet MAC:
Media Access Control: CSMA/CD (wired Ethernet)
1) Carrier Sense (CS):
listen on bus, only transmit when no other signals are detected.

2) Multiple Access (MA):
multiple devices access the same medium.

3) Collision Detection (CD):
when a signal other than own is detected, send a jam signal (so all devices detect a collision), all signals wait a random time before re-transmitting.

Media Access Control: CSMA/CA (WLAN - wireless local area network)
Problems in WLAN if CSMA/CD MAC is used: hiden node problem. Wireless devices maybe far apart and may not be able to detect other devices. 
Solution: CSMA/CA (1. ARQ; 2. Controlled Access).
1. stop-and-wait ARQ (1 and 2 are somehow similar)
- automatic repeat ReQuest.
- receiver sends ACK (acknowledged) after receiving a frame. Sender does not send the next frame until an ACK is received.
- if no ACK is received, everyone waits 0 to 1, 3, 7, ... time units before re-transmitting (exponential back-off).

2. controlled access
- device can send RTS (request to send). device only send after receiving CTS (clear to send).

