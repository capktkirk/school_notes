Program 3 due Nov 1st.

Lab this week is TCP

Distance Vector : RIP (Routing Information Protocol)
* Each network maintains a network map that is centralized from the router itself.
* Each router needs to know the cost to talk to its immediate neighbors.

When A talks to F it doesn't broadcast F on the table.

Heartbeat updates and Triggered updates (for maintaining network map.)

*Link-State Routing* : Algorithm

A->E(1)
A->F(1)
A->B(1)
A->C(1)

Suppose A->E goes down.
A->E(INF)
C->E(2A)
B->E(2A)
F->E(2A)

The table would completely melt down and "Count to Infinity" and never send the packet.

RIP Solution  : Make Infinity = 16
              : Only advertise new information, and not routes from origin. (C->E through A, C does not tell A 
                about it's own routes.
              : The above is called "Split Horizon"

              : Poison Reverse : Intentionally sabotages tables that have identical data through a 
                route for a changed table. Any route that is larger than most effective route is "poisoned"
                to be larger than it actually is to keep it from being interrogated.

Packets only contain information useful to the router that is receiving it.

When you remove a cable why doesn't it count to infinity : Because the split horizon and "poisoned reverse" and small infinity

Section 5.1
*Link-State Routing*
-> Open Shortest Path First
-> Similar Assumptions
  * Each node knows the state of the neighbor. (Up or Down)
  * Cost of each link is known.
  * Directly connected neighbors we know how to access.

Next Step : Sharing info with neighbors.
  * Reliable Flooding. (Everyone gets the info from the node that is connected. Reliable ensures that the info
                        gets out.)
  * Link State Packet : ID of node that created the packet.
                        List of neighbors/costs
                        Sequence Number
                        Time To Live
  * ID and List         -> Routing Calculations
  * Sequence and TTL    -> Reliable Flooding : Sequence : Packet old or new. TTL prevents long life of packets.
