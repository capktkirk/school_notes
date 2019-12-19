Programs 4 and 5 :

Same group. They build off of each other.

Server and Client stuff. Implement ARQ, ARQ with packet loss.

Flags.

SYN flag and FIN flag and ACK

TCP is full duplex.

A -> B (Data ACK-B)
A <- B (Data ACK-A)

Keeping track of Aseq and Bseq.

TCP Set up sequence looks like :

State Machine : A way to define a different condition or operating conditions that the protocol will do at different stages.

TCP Three-way Handshake :
  * Run a TCP connection on wireshark.
  * Client - Server perspective (Set up):
    * Server waits.
    * Client sends SYN (Sync) with a sequence number (SYN,Seq, x)
      * Sequence # is usually the clients sequence number.
    * server sends back a (SYN, ACK, y) y = server sequence number
    * Client then sends an ACK to server, (ACK, y+1) waiting for next
      sequence.

  * TCP 3-Way handshake Tear Down :
    * At some point someone is going to send a FIN (finished signal)
    * Client sends FIN
    * Server ACKS back with it's own FIN.
    * Sometimes client sends ACK that it got the FIN.


  ##More info on set up.

  * Exchange starting sequence #'s
    * Choose random #'s to start the sequence to prevent spoofing; 
      partially. 
    * Wireshark lists Relative Sequence Number (To the first packet)
  * Next Exchange : Advertised Windows. (Byte size)
    * In TCP it is Bytes, not packets.
    * TCP Guarantees an uninterrupted stream of bytes.
  * You could also exchange unique data for setting up TCP


Full Example of a Stream :

Example ACK = What next to give.
Host ->   (Syn i)                  -> Server
Host <-   Syn(j), ACK( i + 1)      <- Server
Host ->   ACK = j+1                -> Server
Host <-   Data, ACK(i+1), SEQ(j+1) <- Server
Host ->   ACK(j+2)                 -> Server
Host ->   FIN, ACK(j+2)            -> Server
Host <-   FIN                      <- Server

ARQ deals with the complications and how to fix the complications.
Work with ARQ in case of pocket loss.

##Sequence Numbers :
  The Sequence Number field in TCP : 32 bits long. (2^32)
  Roll over/Wrap around of sequence numbers.
  TCP does what to give me next, so you can tell when things are needed.


Remmber that we allow an out of order packet to arrive up to 120 seconds later. Modern Internet Speeds have messed up the whole 120 seconds being 2^32 packets in a 120 second window.


Timeout timers and RTT
ARQ A->B would be one RTT (But that can vary and cause problems)

TCP RTT needs to be adaptive.
  * Allows for changing network conditions to not do a resend.

One Solution : Exponential Backoff : Waits a little longer than RTT to see if the packet arrives, if it does change the RTT to some limit (arbitrary)
* Solved major internet congestion in the 80s
* 


