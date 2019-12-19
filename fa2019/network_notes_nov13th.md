Stop and Wait ARQ

Server sends packet, client waits for packet.
Client sends ACK (Saying it has been received)
If client DOESN'T get a packet, no ACK is sent.
If no ACK comes back, server automatically RESENDS

Timeout value of 50 ms

Client :
while(recv ... ){
wait
if(getpacket){
sendACK
}
}

Server :

//Deals with dropped packets by waiting for 50ms.
//Server waits conditionally with select.

select() is how we're going to do timeout value. (RTT)

If no ACK (resend)

##Problems on Client Side :

Server sends packet to Client
Client sends ACK, but it is longer than timeout
Server resends.

Client doesn't know because it is duplicate data.

Client needs to have a sequence number.
char buf[256]
You can take one byte and make it your sequence number.
Only dealing with one packet in time at a time, store sequence number to check if packet has been resent.

###Problems on Server Side :

###HINTS

Suggest be careful about what functions you use.
Do not use string functions to handle file data
fgets, fputs reads things as strings.
use function read/write
Watchout for sequence number on the file.

copy data from buffer into buf2 write out with length - 1

turn the beginning packet of the buf is the sequence number.
