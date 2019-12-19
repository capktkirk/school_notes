CH 3.2.1 -> CH 3.2.2 (Not on the Exam)

Next Section : 3.2.3 -> 3.2.5

UP another layer (layer 3: Networking Layer)

Physical Layer
Data Link Layer
Networking Layer
Transport Layer
Session Layer
Presentation Layer

New Protocols : 
  * IP (Internet Protocols)
  * ARP (Address Resolution Protocol)
  * Routing
  * ICMP (Internet Control Message Protocol)
  * TCP, UDP (Transmission Control Protocol and User Datagram Protocol)

There is a cost (more data transfer, more latency, and more programming)


##Network Abstraction
  * What is a network
  * Where are the boundaries for a network.
  * How to get outside of the network.
  * (the www addresses are for people, the actual address is an IP.)
  * You get this via DNS.

###Exam on monday. 

Formula's to know : Data/Rate + Propogation Delay (Latency)
D/R is Transmission Time 
P -> Delay from sending message to the receiver getting it. 

L = D/R + P
Latency = Time

Throughput        : Amount of Data / Time (A rate)
Throughput        : Data/Latency
Goodput           : Payload/Latency
Store and Forward : Additional source of latency

##Examples :
A -> B (simple)
A -> switch1 -> B (slightly more complex, and the latency between A -> switch1 and switch1 -> B may be different)

Store and Forward Example :

A->S1 = (D/R + Propogation Time)
S1    = St&Fo
S1->B = (D/R + Propogation Time)

Throughput = D/Latency(tot)
RTT : Roughly 2 (Latency(tot))
Good practice ones : (HW1 Problem 6)


