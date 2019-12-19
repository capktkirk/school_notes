Lab 8 only uses internal network.

Static Routing :
Dest Net : DesNetMask : Next Hop (The next place it knows it can go to.)

10.11.0.1 <- 10.11.50.1 (Static Route to the internet)
Need another route to reach Desk Z
10.11.50.1 -> 10.11.50.26

Problems with Static Routing :
  * A lot of maintaining the database.
  * Route are hardcoded by hand.
  * Issues when you add or remove a router (intentionally or otherwise.)
  * Can't detect that a router died.


Routing (Dynamic) : It is in essence the problem of graph theory.

Dykstra's and BST (graphs)

Basics of Graph Theory :
  * Nodes and Edges
  * Node = Routers
  * Edges = Connections
  * Switches are on the 2nd Layer of the Networking Layer Model (Ethernet)
  * Routers are on the 3rd layer of the Networking Model (IP Layer)
  * We can apply costs/weights to the edges. This allows us to find the best route.
  * Route determination must be done by each router :
    This is a distributed system.
  * Alternatively, a centralized system is one where a single device governs the pathing of all the others.
    Collects the data on weights and figures out the fastest route.
  * Proactive System vs. Reactive System.
    * Proactive :
      * Constantly send updates.
      * Con : Constantly spamming the system.
      * Pro : Steady flow of packets. We know the cost, even if it is higher.
    * Reactive :
      * Only sends updates when there is a change.
      * Con : Might not be able to react in time or deaths on system aren't monitored.
      * When there is a change we flood the network with the update. Unpredictable.

Metrics in Network Design :
  * Communication Overhead
  * Computational Complexity
  * Storage Overhead (for all routes)
  * Resiliency
  * Convergence Time (The time that it takes for the network to stabilize after a change.)

  * *Distance Vector* : Algorithm
  * *RIP* : Networking Protocol (Routing Informational Protocol) :
    * Each router maintains a network map that is centralized from the router itself. 
      One dimensional array (The vector) of distances (cost to talk to each router in the vector)
    * Each router in the network needs to know the cost to talk to its immediate neighbors.
    * You can either customer configure the costs, have them be arbitrary, etc. Up to the
      network designer.
    * Link Costs : If we starting the protocol from scratch, any device that is not directly 
      connected is said to be at cost "Infinity" thus precluding it from being picked as a route from
      the router. If a device becomes unreachable, it returns to the infinite state.
      * After startup the routers are going to start sharing information. They're going to share to their 
        immediate neighbors who they are connected to and what the cost is.
    * Problems with Distance Vector : Uses periodic updates, and triggered updates. 
      * Periodic Update : Heartbeat update
      * When that update stops, it triggers another type of update.
*Link-state Routing* : (Algorithm)
