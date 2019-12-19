Exam 1 Topics :

Switch Routing
There is a link on Blackboard.

RTT : Latency * 2 (one way)
Bandwidth * Delay is the Bandwidth Delay product

Physical Layer
Data Link Layer
Networking Layer
Transport Layer
Session Layer
Presentation Layer
Application Layer

Encapsulation


Broadcast Storm
STP concepts this week.

*Lab 5* :
  I/O (Use the I/O in the lab.)
  read, open, write functionality
  strings in C contain a null terminating character. '\o'
  We don't want to use strings, don't treat it as strings, treat it as arrays of characters.
  One check off. Turn in your program and associated Makefile through Learn (for lab 5)

  First part is just read/write/open
  Second part is taking pdf and downloading it then doing a sed -e check

_Program 2 : File Transfer Protocol_
  *May be able to use the streamtalk server and client for TCP*


_*You can test this on the same computer.*_

File in two different directories. In two different terminals.

Terminal 1 : Dir1 and Client.c
Terminal 2 : Dir2 and Server.c

--------- Back to Switches : ------------

Static  -> Hard coded : Manually updating.
Dynamic -> Soft coded : Automatically updates when a node makes a request.

Networking Loops :
  Bad, but we sometimes need redundant connections.

  If A is attached to two switches and those two switches are also attached to B, it will
  create a "Broadcast Storm" and wait for B to update the table. If B never responds the network will
  continue to bomb the system.

  * Ways to fix this we have.

  Spanning Tree Protocol :
    * We're going to form a "tree" of the network switches.
    * One of the switches get picked to be *Root*.
    * STP - Spanning Tree Packets.
    * Packets route without loops, if the Spanning Tree is built correctly.
    * Each switch is going to pick a port that takes it closest to the Root.(This way it knows if
      it is going up towards the Root or down the tree.)
    * Any port that goes to the Root other than the main port gets blocked or turned off.
    * All this information is shared to build the tree via a Bridge Protocol Data Unit (BPDU)


    _How do we pick_ *Root*_?_
    * Assign or use preconfigured ID's if you're hard coding it.
      * Lowest ID Number wins and becomes Root --> BUT
      * It needs to be the most efficient configuration for the needs.
      * No account is given to the physical network setup.
      * If two nodes/switches have the same ID, the tie breaker will be a MAC address.

    * Convergance time is how long it takes to get from on to stable.
    * This happens when a new switch is added or a network change happens. The STP needs to be
      repopulated.
    * STP is slow because of the way it is.

  *STP VARIATIONS*
  * Rapid STP is a variation, but it still has problems.
    * Say the devices are spread out, A -> C need to talk but B -> D are talking, you'll need to
      wait.
  * Multiple STP : Multiple STP maps that be used to avoid traffic congestion.
  * Shortest Path Bridging : Deals with the issu eof "How do I give some routing structure to my network
    so I'm not trying to route through the tree inefficently."
    * Also deals with routing cost and multiple equal cost routes.

We end up with broadcast storms because w edon't have a way to kill packets. We use STP to control the life of packets.

