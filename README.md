# FIT1047-Intro-Computer-System-and-Security-Revision



## Week3
[MARIE](https://github.com/MARIE-js/MARIE.js) Registers
AC (Accumulator): a "general purpose" register, stores the value currently operating on.
MAR (Memory address register): stores the memory address.
MBR (Memory buffer register): stores the data when being transferred.
IR (Instruction register): current instruction being executed.
PC (Program counter): where the program is in its current program sequence.

Combinational circuit:
Output is a function of inputs.

Examples of combinational circuit
adder: add two bits. Truth table components - bit1, bit2, result, carry.
full adder: add three bits. Truth table components - bit1, bit2, carry in, result, carry out.
ripple carry adder: connect three full adders. 
decoder: activate one output based on two bits.
Multiplexer: select one of several inputs.

Arithmetic logic unit (ALU) 
computations:
- integer operations (addition, subtraction, multiplication, division).
- comparisons.
- bitwise boolean operations (and, or, not).
- shifting.

Inputs:
- two n-bit operands.
- op-code (which opeartions should we do?).

Output:
- n-bit result, status flag (error, overflow, success).

How ALU decide which operation to use?
- Do all operations in parallel.
- Choose the one described by op-code, using multiplexer.

Sequential Circuits:
Output depends on a sequence of inputs.

Examples of Sequential Circuits:
- SR latch (set-reset-latch).
- D flip-flop. 1) one input: the data to be stored. 2) one output: the data currently stored. 3) a clock: state only changes on "positive edge" (clock can be configured to positive edge or negative edge). * application: register design.

Register transfer language (RTL)
Fetch:
4 steps.

Decode:
0, or 1, or 2 steps.

Execute:
0, or 1, ..., or * steps. Depends on implementation.



## Week4
When does CPU communicaite with I/O devices?
Programmed I/O:
a.k.a., polling I/O. Program checks registers periodically.

Pseudocode Programmed I/O:
while (true):
    if (IORegister1.canRead()):
        processRegister1();
    else if (IORegister2.canRead()):
        processRegister2();
    else if (IORegister3.canRead()):
        processRegister3();
    ...
    end if
end while

Interrupts (opposite of polling):
- CPU is notified when I/O is available.
- CPU interrupts what it is doing, process IO, then continue with normal opeartions.

How CPU is notified of I/O?
- Device notifies CPU of interrupt by setting a bit in a special register.
- algorithm {cpu checks if the interrupt bit is set. If yes process interrupt, else fetch-decode-fetch}




## Week7
Symmetric encryption:
sender and receiver share the same key to encrypt (lock a padlock) and decrypt (unlock a padlock) the transmitted messages.

Disadvantages of symmetric encryption:
- key distribution. A secure channel is necessary for the distribution of secret key (recursive problem: need to create a second channel that is secure).
- scalbbility. Each pair of sender and receiver needs to have a unique pair of key (otherwise one gets hacked => all gets hacked), and the number of keys grow exponentially. e.g., 2 people have 1 handshake, 3 people have 3 handshakes, ..., 10 people have 45 handshakes.

Public key cryptography (asymmetric):
Sender can encrypt a message (lock a padlock) using the public key of the receiver, but only the receiver can decrypt (unlock the padlock) using the private key of his own. Private key is kept by the receiver and nobody knows what it is.

Crytographic hash function:
- a hash function maps input of arbitrary length to a fixed length output.
- cryptographic hash functions are infeasible to invert.
- hashes for similar messages should not be correlated at all.
- infeasible to find collisions - two messges with the same hash value.
- used to in digital signatures, for storing password, MAC (message authentic code).

Message authentication code:
- also known as a 'tag', is a short piece of information used to authenticate a message. That is, to authenticate the message comes from an authenticated sender (authenticity) and the message has not been changed (integrity).
- consists of three algorithms. 1) A key generation algorithm selects a key from the key space randomly. 2) A signing algorithm efficiently returns the tag given the key and the message. 3) A verification algorithm that efficiently verifies the authenticity of the message given the key and tag. That is, return Accept when the message and tag are not forged and Reject otherwise.



## Week8
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



## Week9
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



## Week10
IP version 4 address
- used to address network layer devices (Each network layer device has its assgined IP address).
- Example: 130.194.66.43
10000010 11000010 01000010 00101011
networknetworknet subnet(LAN)Hostho

how a router works: A router connects two or more networks. If a device sends a packet to another device that is not under same subnet, the 1st device must send packet to its gateway router and then send to the 2nd device's gateway router under the same subnet. Lastly the packet is sent from the 2nd gateway router to the 2nd device it connects to.

how a switch works: A switch connects devices in a LAN. When a packet arrives, switch looks at forwarding table to decide which port the device with the destination MAC address is connected to. If MAC-port pair does not exist, the packet will be sent to all ports and remember which port the packet goes to. If MAC-port does exist, then (great!) send the packet to its port directly.

Backbone networks: a backbone network interconnects various pieces of networks, providing a path for exchanging information between LANs and subnetworks.

Address resolution @applicationLayer
How to find MAC address for an IP address: devices keep a mapping between IPs to MACs. the router will ask the switch every client is connected to with MAC address as an input. Switch will return an IP address the input MAC address is mapped to as an output.

One address per network layer (what is the address and what it does)
Application layer: 
URL. Identify and access network resources that are connected to World Wide Web.

Transport layer (TCP):
port number. Identify which application on a certain device to send packets to.

Network layer (IP):
IP address. Identify which device to send packets to.

Data link layer:
MAC address (48 bit - 6 bytes. e.g., MM:AA:QQ:WW:FF:EE). Identify which switch to send frames to.

Each TCP packet contains two numbers.
1) sequence number.
how many bytes we have transmitted.

2) acknowledgement number.
how many bytes of acknowledgement we have received from receiver.

* Motivation:
we can therefore check how many bytes of data we have transmitted successfully.

Establish TCP connection
some terms:
- @SYN indicate to start a TCP session.
- @ACK indicate to ackonwledge the recipient of transmitted packets. 

three-way handshake:
- client sends a SYN packet, with a random sequence number A
- server replies with SYN, ACK, acknowledgement number A+1, and a random sequence number B.
- client sends ACK, acknowledgement number B+1.

Close TCP connection
four-way handshake:
- computer A (client or server) sends a FIN packet
- computer B acknowledges with an ACK
- computer B sends a FIN packet
- computer A acknowledges with an ACK 
* can be simplified to a three-way handshake (combing B's ACK and FIN)

Internet architecture
- The internet is a network of networks.
- Each network is an automous system operated by an organizaiton or ISP (internet service provider).
- Within an automous system, routers exchange packets/information/data via "interior routing" (protocols: RIP, OSPF, EIGRP).
- Outside an automous system, an automous system pair exchange information via a border router - "exterior routing" (protocols: BGP - border gateway protocol).

## Week11
Trusted certificates:
- A trusted certificate is digitally signed by a known certification authority.
- Browsers (e.g., Chrome, Safari, Firefox) have a list of known certification authorities.

Problems with certificate:
- Each browser has a long list of trusted certificates. But it is unclear whether those certificates are trustworthy.
- Everyone can buy certificates for their website, but it does not make the certificate trustworthy.

VPN: A VPN connects a client to VPN gateway via encrypted VPN tunnel.

why VPN does not provide end-to-end security between a home PC and a PC in an enterprise network: because the encrypted tunnel ends at VPN gateway. It does not extend to the enterprise network.

DMZ (demiltarized zone):
- Create a zone that considered less secure than internal network, but still protected from direct access. It is a zone that lies between an internal network and the internet.

Examples of firewall placements for DMZ:
- A DMZ can be realized with one firewall (three-legged). One leg is the DMA, the 2nd leg is the internet, and the 3rd leg is the internal network.
- A DMZ can be realized with two firewalls (and is more secure). One towards the internet and another one towards the internal network.

IDS (intrusion detection system):
It monitors network and system activities. Once a potentially malicious activity is found, alert the system.

IPS (intrusion prevention system):
It is an IDS with additional active functionality. It blocks or stops potentially malicious activities.

## Week12
Security properties
authenticity: data is from the source where it claims to be from.

integrity: data has not been changed since last authentic event.

confidentiality: data is kept to some principals only.

privacy: the protection of personal informations/space (account, password).

availability: some service or resource can be used within a particular time with a particular quality.

non-repudiation: some action is related to an entity, and there is evidence that it has actually happened. Thus, this entity cannot repudiate what is happened. e.g., a signed contract.

Security attacks
worm: a standalone malware program that replicates itself, and trys to spread to other computers or networks. e.g., file transfers.

virus: a standalone malware program that replicates itself, and insert codes into computer system in order to exploit system weakness. Get distributed with program/document. Runs and spread when host program executes.

trojan horse: a program that hides itself from its true intents, create backdoors to give attacker access, activate other malwares.

phishing: create a fake login in page and steal internet users' credentials.

ransomware: install malicious programs that encrypt data, and ask for money (professionally). 

botnets: remote control, run denial of service attacks that prevents system from working. e.g., from inside of a computer using virus, trojan horse. Or from outside of a computer using massive requests/traffics.

## Sample exam

