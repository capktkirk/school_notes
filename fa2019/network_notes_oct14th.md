propogation delay : time for 1st bit of transmission to the last bit.

IPv6 -> 128 bytes.

Contains all IPv4 Addresses :

128.64.31.5

becomes

::FFFF:8040:1505
      | above   |
      | address |

Other import things about IPv6 :
  * Loopback address has changed.
    * ::1
  * Local link only
    * FE80:: Anything starting with this is local link only.

  * Changes to the Header :
    * Took out the checksum
    * TTL -> Hop Limits

    * Took out the ability to fragment packets (No "No Fragmentation" option)

    * Addresses are determined without DHCP :
      * Now when they join, they autoconfigure with ICMPv6 to find unused 
        addresses.
    * Means the router handles the configuration rather than the device.
    * The router also provides solicitation (lets people know it is the 
      edge gateway. Router Solicitation.

    * No more ARP. Instead use Neighbor Discovery Protocol (NDP)
      * Similar to ARP (Maybe less vulnerable.)
      * Devices actively discover who is in the network.

    * Security built in, uses IPSEC (IP Security) uses VPNs.
    * Support for Mobile Routing (How you move from one wireless network to another.)

###Next Topic : Routing

In Section : 3.3.1 then go to 3.3.2

Lab this week : Static Routing with Kredo


Static Routing :

  * Hard Coded Path to a destination
    * Manually saying how to get from A to B
    * Bad (Don't do this in the real world.)
  * Define Static Route : 




     _______________________________________
    |                                       |
    |                                       |
    |                                       |
    |                                       |
    |                                       |
    | _____________________________________ |

   Lab 4 :
   10.11.0.0/ is the upper side
   192.168.1.24 is the lower router
   192.168.1.0 is the network overall.
   Anything in the overall network has the IP address in the 192.168 range.
   To get to the internet we need a default gateway to the internet.

  Anytime something doesn't know what to do with a packet it'll pass it to a default gateway (kick 
  the can down the road).

  Desk Z has it's own network. (192.168.26.0/24)
  Desk Z Default Gateway : 10.11.50.26
  We can't get there through the default gateway.

  static route contains :
    Destination network
    Destination network mask
    Next Hop. (One step closer to the edge, I'm about to break.)

  PCZ -> Destination Network : 192.168.26.0
         Destination Mask    : 255.255.255.0
         Next Hop            : 10.11.50.26

  PCA -> Destination Network : 192.168.27.0
         Destination Mask    : 255.255.255.0
         Next Hop            : 10.11.50.26

  (Daisy Chain : Destination shows where we want to go, next hop will be the next pass off.)

  Everything needs a static route.


  192.168.1.0/24 -> 10.11.0.0/16 -> 192.168.26.1/24 -> 192.168.27.0
  It has to go back the same way.
