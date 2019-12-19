Submissions script not yet known.

Link State Routing : OSPF Open Shorted Path First
diff to vector distance
* reliable flooding
  * Sends out link state packets (contain ID, neighbors, costs, sequence number and a TTL)
* Update spreads as evenly as possible.
* UPdates Occur under two conditions :
  * Periodic Generation of Updates (heartbeat)
  * Topographical change (change to network.)

Route Calculation uses : Dijkstra's algorithm
Make Two Columns (First Column Confirmed Paths : Second Tentative)

Example : 
A-> B(5), C(10)
B-> A(5), C(3)
C-> A(10), B(3)
D-> B(11), C(2)

    A Table
| Confirmed Paths               | Tentative       |
| (A,0,-)                       | (B,5,B)(C,10,C) |
|                               |                 |
| (A,0,1)(B,5,B)                | Updates         |
|                               | (C,8,B)(D,16,B) |
| (A,0,1)(B,5,B)(C,8,B)         |                 |
|                               | (D,10,C)        |
| (A,0,1)(B,5,B)(C,8,B)(D,10,C) |                 |

The pathing ensures the best cost at the shortest route. (Djikstra's)

| (B,0,-)               | (A,5,A)(C,3,C)(D,11,D) |
| (B,0,-)(C,3,C)        |                        |
|                       | (A,5,A)(D,5,C)         |
| (B,0,-)(C,3,C)(A,5,A) |                        |
|                       |                        |

Next week doing the OSP

Let's talk bigger :
  Larger Networks (Continental sized)
  * BGP (Border Gateway Protocol)
    * Designed to work with an autonomous system.
    * Collection of IP addresses or prefixes that have been bundled together (multiple networks)
    * Capable of multipathing and multiprotocol functionality.
    * Traffic gets assigned Autonomous Number systems (Each AS has a different number associated with it)
    * That additional address is used to connect traffic between autonomous systems.
    * It makes it work with Path Vector Routing
    * Previously : OSPF and RIP we developed the path as we ran the protocol
    * Path Vector Routing assigns the path to how you want to route.
    * Think of the entries : 
        Router Entries will contain : Destination and Network, Nexthop to send to, and Path to destination
    * 
