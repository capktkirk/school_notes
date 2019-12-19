
Classless Inter-Domain Routing (CIDR)
-no longer have to buy a ton of different IP addresses (not done by class
anymore).
- allows for subnetting
    - 10.0.0/8
    - 10.11.0.0/16 <-- this is a subnet of the one above

subnetting is neat, but it creates some issues
for example, if you are routing, with subnetting, you can end up with very 
long routing tables.
to get around this, they also implemented LONGEST PREFIX MATCHING within
CIDR.
this allows us to aggregate routes
to do this, we look at all the addresses on the network
and pair them by matching bits.
if i have 16 addresses, 192.4.16.0 -> 192.4.31.0
the first 20 bits will match.


forwarding priniciples in IP
-routers maintain a table

destination network |  destination net mask | next hop 

*the next hop device is the device that can get me one step closer

forwarding
----------
if a packet destination is local network, we send it
if a packet is for a different network:
  - if host, send to default route
  - if router, check forwarding table or port IP
      - if table - send it
      - if port, send out port
      - also has a default route


IPv4 header
----------
-can hold version (IPv4, IPV6, but we're mainly focusing on ipv4)
-internet header length (ethernet header length is fixed, internet header
is not) (abbreviated IHL)
- differentiated services code point (DSCP)
  - used to classify network traffic
- explicit congestion notification (ECN)
  - allows us to notify endpoints about congestion in the network
- total length
- identification
  - used to 'glue' packets back together (recompile a broken up packet)
  - think of it as 'grouping' -- but there is a separate field that tells
    us where they go in the group
- fragment offset field 
    - refragments the group into proper order
- flags
  - could or could not be used
    -  do not fragment is an example of a flag
- time to live (TTL)
  - hop time counter. counter decrements after each hop.
  - if counter reaches 0, kill packet
- header checksum
- SRC/DEST IP addresses
- options (variable, can be left out of the header)


how does layer 2 interact with layer 3 (ethernet to up)

TRACEROUTE (con't)
-----------------
*question 14 on lab 7 
- address resolution protocal (ARP)
  - finds a MAC address given an IP address
  - when you try to ping somebody, the first thing that goes out is an ARP
    request. b/c in a layer 2 network we route by ethernet but ping works on
level 3. 

  - ARP request is a broadcast request. 
  - there is an inherent flaw with ARP requests, because they rely on trust.
    - A could send a packet to B, but because it's a broadcast, and if there is
      a bad actor there, then that bad actor could respond before B does, then
      A will think that bad-actor is B, can spoof A and B can reply...

  - this is what a man-in-the-middle attack is.





*helpful for project 2--
place client and server in separate directories
 ./server 5555
 ./client 127.0.0.1 5555 <-- 127 is for working on home machine

