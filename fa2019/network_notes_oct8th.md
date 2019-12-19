Networking.

Server code p2 :

if the server can read the file, then send the file to the client and quit.

How to run test_script from Kredo.

Makefile will need to be uncommented:


Server Code P2 :
  connect
    cmd arg port#
  wait for filename (recv request)
  if(open[checking]){
  }
  if else(note there){
    send error and quit
  }
  else{
    while ((len = read(buf)) > 0){
      len = read(buf)
      send_to_client(buf, len)
      //pick a value and leave it.
  }

Client Code p2 :
  connect(ip address, port#)
  (ip for local testing -> 127.0.0.1)
  send(filename, len(filename))
  //test to print the filename you've got in.
  //print strlen return as well.
  recv()
  if(err){
    quit gracefully.
  }
  else{
    //only open file when a file is there to receive.
    open.file();
    write(filename, buf from recv)
    while{
    recv
    write
    //until done.
    }
  }


In our devices there is an ARP table (Cache)

A man in the middle attack ARP protects from.

A ---- (S) ----- B
        |
        C

C lies that it is B, and connects to A.

ARP Cache poisoning. : Sometimes we do want to intentionally do this.

Vulnerability in layer 2.

ICMP : Internet Control Message Protocol (error messages, configure, diagnostics.)
Common Examples : Echo(ping)
                  Unreachable Network or Host
                  Redirection
                  TTL has expired (Time to live : Packet died on the internet)
                  some devices intentionally turn this off.

Traceroute : Traces the hops (Max 30).
  * To do this takes advantage of :
    * ICMP
    * Limited TTL
Traceroute starts at TTL = 1, when it dies an ICMP is sent back and they use these to map
to the destination.

Three asteriks sent back mean that the host doesn't want to send back the IP to Traceroute. (Security/Privacy reasons.)

DHCP -> Dynamic Host Configuration Protocol

  * Dynamically manages host/IP masks/gateways/ETC
  * Process :
    * Discovery/Find local DHCP server
    * Offer configuration to computer(IP Mask/Gateway)
    * (Optional : Request specific configurations)
    * ACK : Acknowledge the acceptance of the request.

NAT -> Network Address Translation
DNS

IPv6 :
  * IPv4 -> 32 bit address (2^32 == 4.3 Billion)
  * IPv6 -> 128 bit address (2^128 == 3.4 x 10^38 addresses)
  * Hex Representation
  * Fe80:0000:0000:0000:0250:56FF:FEC0:0008
  * You can use :: to condense 0s
  * FE80::250:56FF:FEC0:0008
  * FE80::250:56FF:FEC0:8


