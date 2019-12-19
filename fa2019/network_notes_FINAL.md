Exam Topics :

  *UDP* :

    Connectionless.
    Packets can arrive out of order
    Not reliable
    Byte Stream
    Why use UDP? :
      * Use when speed is more critical than reliability.
  ## *TCP* :

    Connection based (sockets, accept/request)
    Reliable :
      How is this achieved?
        * Acknowledgements and Retransmissions
        * TCP Three-Way handshake (Startup):
          * Server waits, client sends SYN(Sync) with a sequence number
          * Server sends back a (SYN, ACK, y) which is the server sequence.
          * Client then sends an ACK to server (ACK, y+1) waiting for next sequence.
        * TCP Three-Way teardown :
          * Someone sends a FIN (finished signal)
          * Client sends FIN
          * Server ACKS back with it's own FIN
          * sometimes client sends ACK that it got the FIN
    *Congestion Control* :
      How does TCP calculate RTT?
        * Initial RTT is calculated via the threeway Handshake (Described above)
        * Exponential Backoff : Waits a little longer than RTT to see if the packet arrives, if it does change the RTT to some arbitrary limit.
        * Adaptive Timeout : See Exponential Backoff above, it changes the timeout based off of Initial RTT.
        * ACK is a receipt of Delivery, not a time stamp
        * Additive Increase/Multiplicative Decrease : A feedback control algorithm best known in TCP. Increase the transmission rate (window size), probing for usable bandwidth until loss occurs. When congestion is detected the transmitter decreases teh transmission rate by a multiplicative factor; for example cut the congestion window in half after loss.
      Sliding Window Concept in TCP (bytes not packets)
        * Data is seen as a transmitted byte stream, packets transmitted in reality.
        * Both sender and receiver maintain a window size. The window size is the number of bytes they will send or receive at a time.
        * The window of both the sender and the receiver moves as the data is successfully sent between them.
        * This requires setup prior to the transmission of data.
      *ARQ and Sequence Number Concepts in TCP* :
        * Stop-And-Wait ARQ :
          * Wait some amount of time for an ACK to arrive
          * When the ACK does arrive in time, send next packet. If it does not arrive in time resend packet.
          * Also understand what cases there can be with this form of ARQ and how to represent them.
        * Cumulative ACK :
          * Ties into the sliding window concept.
          * Allows for multiple packets to be in flight at the same time.
          * ACK the last receved packet that has arrived correctly :
            * EX. packets 1, 2, 3 and 5 arrive, ACK packet 3, tells sender to resend packets 4 & 5.
          * Selective ACK variation :
            * ACK only missing packets. Using the above packet example, the ACK would be of packet 4 which had not arrived.
            * Be able to explain what is happening given some set of transmissions for Selective ACK.
        * What are sequence numbers used for :
          * What problems do they fix : They allow for dropped transmissions to be fixed more easily. Know the order in which to reconstruct data.
          * How is the starting sequence number chosen : It is arbitrary but low enough to cause less roll-over or at least with a large enough area.
        * Problems with wraparound of sequence numbers in TCP,, especially with modern faster internet connections.

    *Types of TCP packets* :
      * SYN, ACK, FIN, don't worry about the other.

    *Connection Setup* : Threeway handshake mentioned above.
    TCP Transmission process with one server and one client (as shown above.)

  ## *HTTP*
  
    * What is HTTP used for : HTTP is the underlying protocol used for the WWW and defines how messages are formatted and transmitted.
    * HTTP request format :
      * Method    URI   version
      * double carriage return \n\r \n\r
    * Three most common HTTP operations :
      * POST
      * GET
      * HEAD
    * Response codes : 
      1xx INFORMATIONAL
      2xx SUCCESS
      3xx REDIRECTION
      4xx CLIENT ERROR
      5xx SERVER ERROR
    * Caching HTTP
      Benefits and reasons why :
      * Reduces bandwidth consumption
      * Reduces access latency :
        * Frequently accessed documents are fetched from nearby proxy cache
        * Reduce network traffic
      * Reduces the workload of the remote web server by spreading the data widely among proxy caches.
      * If a remote server is not available, the client can obtained a cached copy.
      Cons :
        Stale data, access latency, single-proxy is a bottleneck, and a point of failure.
    * HTTP versions :
      * Difference between 1.0 and 1.1 :
        * Improvements from 1.1
        * Persistent connection : Instead of opening, connecting and sending, it instead creates an open socket.
        * Request pipelining : Multiple HTTP requests can be sent on a single TCP onnection without waiting for
                               a response.
        * Byte serving       :
              HTTP : 1.0 : You get the whole file or none of the file. 
              HTTP : 1.1 : specifiy chunks of the file to get back.
        * Virtual servers : You can have multiple IP addresses on a single server allowing for multiple sites.
        * Content encoding : Compress the HTTP data to increase transfer speeds.

  ## *Security*

    * TLS - Transport Layer Security :
      * The goal of TLS is to provide a secure section for data we don't want to share.
      * Three Parts of TLS : 
        * Confidentiality (Hidden)  - Keys
        * Integrity (Private)       - Hashes
        * Authentication (Verified) - Certificates
      * TLS Sits between HTTP and TCP
      * TLS doesn't change anything between HTTP and TCP, it just takes in info and spits out secure code.
      * At run time a pair of TLS participants negotiate on which cryptography to use :
        * Symmetric Key
        * Public Key
        * Data Integrity
        * TLS will need about 6 Keys :
          * One incoming
          * One outgoing
          * Two for initialization
          * Hash of set up is exchanged to ensure setup integrity
        * Symmetric-Key and Public-key (also called Asymmetric-key) :
          * Pro's and Cons of both methods : 
            Symmetric-Key   : Harder to duplicate, and more "secure" unless you are having to share the key.
            Asymmetric-key  : Also known as Private/Public key. Public key is for unlocking, private key is only accessable by one party.
              Publick ey encrypts.
              Private key decrypts. Only the party with the private key can decrypt.
        * Concept of hashing to maintain integrity :
          * Requires the use of a shared private key to generate secure hashes.
          * Diffie-Hellman Key Exchange : Uses a formula to take a pieces of data and send it so that both the parties can use that formula to decrypt it.
          * Key exchange allows both parties to generate the same secret key mathematically while only having recieved each other's public key.
        * Certificates and Certificate Authorities :
          * Purpose of a certificate : To ensure that the address we are accessing is the actual trustworthy site.
          * Responsibility of a Certificate Authority : To update with the root server, and increase the security of all the traffic to ensure no one is passing back bad information
          * Hacking of CA's and issues this can create : If a CA is hacked, malicious users can reroute traffic to the places that are unsafe.
    ## *DNS -- Domain Name Service*
      * Purpose of DNS : Turning human readable names from IP addresses.
      * Concept as a distributed protocol, no one server has all the information :
        * Requires a processes of looking up result. (Going from root, down to the org, net, com, edu level to the more atomic levels.)
      * DNS caches maintained in local name servers
      * Concept of DNS cache structure, not the exact layout.
        Structured Cache System : Starts at the end.
        www.google.com :
        --------------^ .com is the highest domain
                    Root
                     |
                   / | \
                  /  |  \
                 /   |   \
                /    |    \
               /     |     \
             .org   .com   .net
        .....difference websites with these endings ....
             and before that there are further drilling down of data.
             Root Server -> Name server -> Local server
      * What the process might look like as a client requests the IP address for a domain :
        * Recursive vs. non-recursive :
          * Recursive goes from root, to name server to the local server.
          * Non-Recursive only does the root, unless it is called on a name server but it does not resolve.
          * dig is the command.
          *   <<>> DiG 9.14.8 <<>> www.google.com
              ;; global options: +cmd
              ;; Got answer:
              ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 20200
              ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 5

              ;; OPT PSEUDOSECTION:
              ; EDNS: version: 0, flags:; udp: 4096
              ; COOKIE: ae9105019f242afa88f178295df9853c302e7d2870f61dbb (good)
              ;; QUESTION SECTION:
              //Web Address  - Internet/Name Server - Type
              ;www.google.com.			IN	A

              ;; ANSWER SECTION:
              www.google.com.		184	IN	A	172.217.6.68

              ;; AUTHORITY SECTION:
              google.com.		58421	IN	NS	ns3.google.com.
              google.com.		58421	IN	NS	ns4.google.com.
              google.com.		58421	IN	NS	ns1.google.com.
              google.com.		58421	IN	NS	ns2.google.com.

              ;; ADDITIONAL SECTION:
              ns2.google.com.		58421	IN	A	216.239.34.10
              ns1.google.com.		58421	IN	A	216.239.32.10
              ns3.google.com.		58421	IN	A	216.239.36.10
              ns4.google.com.		58421	IN	A	216.239.38.10

              ;; Query time: 8 msec
              ;; SERVER: 132.241.82.200#53(132.241.82.200)
              ;; WHEN: Tue Dec 17 17:44:17 PST 2019
              ;; MSG SIZE  rcvd: 223


    DNS Vulnerability : DNS is vulnerable because it's relying on a third party to authenticate, which means that a person can cache DNS data locally and get someone to go to a website that might not be the correct website.
