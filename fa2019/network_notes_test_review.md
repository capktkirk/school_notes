Test Review :

Network Layer : Layer 3
  * IPv4 Addresses
    * IP Address Structure (address and mask)
    * Mask formats in slash notation or dot notation
    * Using the mask to obtain the network address
    * Using the mask to obtain the broadcast address
    * Special IP Addresses
      * Broadcast
      * Loop back

Nexthop is one step closer, you should be able to access it in network.

  Historical IP Addresses :
    * Class System. (you do not need to memorize the different class specifics, just know the limitations and organization of the concept.)

  Classless INter-Domain Routing (CIDR)
    * Removed class system
    * Allowed for better use of IPv4
    * Used sub-netting to make smaller networks at will.

Three Ways to Route :
Local Network : Send to device
Remote : Check Forwarding Table.
Default Gateway : if neither of the above work.

Devices :

Z/16 -> A (R1) B -> Y/24 -> C (R2) D -> X/16
Forwarding Table :
  Z -> X
Table :

Dest ---- Mask --- Next Hop
X         /16       C

           14.4.4.7   14.4.4.8
17.7.7.25 (X)------(Y) 15.5.5.7
           |        |
    PC2-   |        | - PC1
           |        |
17.7.7.24 (Z)------(W) 15.5.5.8
         16.6.6.9   16.6.6.13

Dest --- Mask --- Next Hop
17.7.7.0          16.6.6.9
15.5.5.0          16.6.6.13


Understanding what a network is in terms of boundaries and how to join a network .


ARP Poisoning : Falsified ARP messages over a local area network to link an attacker's MAC address with the IP address of a legitimate computer or server on the network.

ICMP : Traceroute to find the route a packet takes.
DHCP : Dynamic Host Configuration Protocol

Routing : 
  Static Routing : What is in a static routing table (DEST_NET, DEST NET_MASK, NEXT_HOP)
  It's bad
  
  Metrics Communication Overhead, Computational Complexity, Storage overhead, Convergence Time (Time to stabilize after a change)
  
  Distance-Vecotr (RIP-Routing INformation Protocol)

OSPF is Djikstra's Distance Vector is different :

Distance Vecotr : Each router sends its neighbors a list of all known networks along with its own distance to each of these networks.

Infinity implies unreachable.


Dijkstra's (OSPF) :


Periodic Update : Heartbeat
Triggered       : Changes or Time Triggered


