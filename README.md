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

Client-based architecture:
client: presentation, application, data access.
server: data storage.
disadvangtages: data is transmitted back and forth between client and server. Creates network bottleneck/loads.

Client-Server architecture:
client: presentation, application.
server: data access, storage.
advangtages: balanced loads between client and server.

Thin-Client architecture:
client: presentation.
server: application, data access, storage.
disadvangtages: 
examples:

Multi-Tier architecture:

Peer-To-Peer architecture:

