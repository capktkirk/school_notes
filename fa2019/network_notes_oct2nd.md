Layer 3 : Network Layer
  * Layer 2 problem:
    * Cannot kill packets.
    * Cannot do complex routing.
    * We cannot do complex routing (Unicast or broadcast or anycast)
  * We are going to introduce and solve these things with IP (Internet Protocol)

  * Model we are going to use for IP : 
    - Connectionless
    - Best Effort
    - We need to have a way to "fail" gracefully, never 100% perfect.
    - build under known limitations.
    - We need a better addressing scheme.
      * We need hierarchy : IP Addresses provide this.
        - They contain routing and network information.
        - They contain:
          - Address
          - Mask
          -> IPv4


A Router is a network Edge Device.
They link networks

IP Address  : ###.###.x.x the two x's pertain to specific device addresses.
            : You can have 2^16 unique devices. (Except for some reserved network addresses)
            : If you do a bitwise AND you can get the subnet from the IP address.

If you do a bitwise OR with the IP address, we'll get the INVERSION of the mask and that is the 
broadcast address.

Historical IP
  * IPv4 Classifications
  * * Classes of IP Addresses
    - A 1.0.0.1 -> 126.255.254 (16Million Hosts, 127 Networks)
    - B 128.1.0.1 -> 191.255.255.254 (65 Thousand per 16,000 networks)
    - C 192.0.0.0 -> 223.255.255.254 (254 Hosts, 2 Million Host)
    - D Multicast Address.

Classless Inter-domain routing (CIDR)
  * got rid of IP classes.


Lab this week, it talks about ipsum or something.

