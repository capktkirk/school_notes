##Switching

[*A*] --------[!]-------------[!]-------- [*C*]
             !               !
             !               !
             !               !
[*B*] --------[!]-------------[!]-------- [*D*]



Packet switching, they can swap up the packet arriving between A and D,
so if 1, 2, 3, 4 packets are sent then it may arrive in a multiple 
variety of orders.

In the switches it will forward and correct this, which is slower than circuit
switching. This means that the switch is analyzing some portion fo the packet;
such as the header to figure out where it goes.

Circuit Switch and this are not great at "Bursty" sending. Ethernet is barebones
routing.

##Virtual Circuit Switching :

We will add more information to the switch for routing purposes.

Forwarding Table :
  Port  | Address
   4    |   A
   3    |   C
        |
        |

      An address can have multiple switches. If bob's PC is putting out data and
      receives data at port 4, it will learn who is connected to it by looking 
      at not only the destination but the source.

      Allow our switches to be more invasive towards the header.

      It could make a virtual connection inside the virtual circuit to an outside
      address for example C.

##Casting (Packets)
  * Broadcast^  (Give a copy of the packet to everyone.)
  * Multicast   (As the network manager, create subsets of groups to
                 broadcast to.)
  * Unicast^    (Singular focus, know the address to broadcast to)
  * Anycast     (There is one destination out of several possible, the
                 routing system determines who gets the packet. See this a lot
                 in ip address.)
  (^ means this will be seen in this class primarily.)

##Learning Switches:

  * Examine the packets that are coming in.
  * Build a forwarding table (As shown above.)
    It will contain two things :
    1. Port that packet came in on.
    2. Address of Packet.
  * You can have additional fields to keep track of, but Port and Address of Packet are
    the bare minimum.

##How do we look at this in an example network :

One Switch. Four Hosts.


A [ ]           [ ] B                     PORT    |     ADDRESS
      \        /                            1     |       A
        SWITCH                              4     |       C
      /        \                                  |
C [ ]           [ ] D                             |

  * A sends a packet to C
  * Switch gets packet
  * updates table
  * Switch broadcasts packet to everyone.
  * Everyone receives packet.
  * Header is checked for destination for 
    addressing.
  * Delete if not for them (B & D)
  * C send a reply that it has been received.
    * If A wants to send another packet to C, it will
      not rebroadcast because it knows C's address.
    * Uni-cast.
  * Switch still doesn't know B & D's address.
  * Now it adds C to the Host Table.
  * A wants to send to D.

##More Complicated Scenario.


A     (1)                       (2) C
       \                      /
        S1 (3)----------(1) S2
       /                      \
B     (2)                       (3) D

S1 Table              S2 Table
Port  | Address      Port | Address
1(s1) | A           1(s2) | A
3(s1) | C           2(s2) | C



* A sends packet to C
* Broadcast to S1 and B, S1 broadcasts it to S2 who broadcasts it to C and D
* S2 broadcasts it to D and C
* C receives it, and sends reply to S2, who sends it to S1, who sends it to A.


##Improved Complexity


A     (1)                       (2) C
       \                      /
        S1 (3)----------(1) S2
       /                      \
B     (2)                       (3) D

S1 Table              S2 Table
Port  | Address      Port | Address
1(s1) | A           1(s2) | A
3(s1) | C           2(s2) | C
3(s1) | D           3(s2) | D


* A -> D
* Sends packet to S1 (broadcast, S2 broadcast)
* D receives it. Sends reply.
* Forwarding tables updated.


##Issues with Switch Learning

If C were to move to 42 on S1, it creates problems.

This needs more sophistication : Delete entries in the table or update them.
* A time-out counter begins ticking after the first packet is received. After a
  certain amount of time they will drop off the table until they begin communicating
  again.

Alternate Scenario :
* C moves to 42.
* C broadcasts to A after table has been updated to erase C's old position.
* We would update because C has a new address it is sending from.

