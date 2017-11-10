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

- error detection.
- 
Contention-based MAC (play by rules)
Any device can transmit at any time:

Collions - two devices tramsmitting at the same time:

Ethernet MAC:
Media Access Control: CSMA/CD
1) Carrier Sense (CS):

2) Multiple Access (MA):

3) Collision Detection (CD):

Shared Ethernet

Problems with shared ethernet
Half-duplex:

Broadcasting:

Limited network size:
