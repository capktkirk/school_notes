Security Plus Book : 

TCP/IP : A group of protocols (A whole suite of protocols) not a single one.

Transmission Control Protocol


Connection (Three way handshake)
TCP client -> Syn -> TCP Server
TCP Client <- Syn/ACK <- TCP Server
TCP Client -> FIN -> TCP Server

UDP is a quick connection, dumps a bunch of data.

ICMP : Sends a ping (doesn't care if it gets returned.)

IP Address dotted-decimal notation
One byte = eight bits
Thirty-two bits (4 x 8) or 4 bytes.

CIDR notation /16 (first most significant bits or the number of significant bits behind the slash.)

IPv6 : 128 bits : Represented by Hexidecimal

ICMP Internet Control Message Protocol : Ping

Encryption Protocols : 

Internet not built with security in mind.

SSH The Secure Shell

Encrypts a wide variety of traffic (SCP Secure Copy)
SFTP Secure File Transfer Protocol 
SSH Uses TCP port 22

SSL (Also known as HTTPS)

Browser connects to a webs erver 
Server sends a copy of the SSL certificate
Browser checks the certificate against a list of trusted CA's
Server decrypts the symmetric session key using its private key and sends back an acknowledgement encrypted with the session key to start the encrypted session
Server and Browser now encrypt all transmitted data with the session key

TLS (New modern SSL)

Uses TCP port 443 when encrypting HTTP
Uses TCP port 465 when encrypting SMTP
uses TCP port 636 when encrypting LDAP

IPSec 

VPN tunnel, encrypts IKE (Internet Key Exchange) negotiation builds the tunnels, IPsec keys used to create ip packets for transporting data, payload encrypted DES, AES or other, data integrity ensured with one-way hash function (MDS, SHA1) fast bulk data transfer.

IPSec native to IPv6 also works with ipv4

Application Protocols and ports
HTTP : port 80
HTTPS port 443 encrypted with TLS
FTP port 20 for data port 21 for control
SFTP - port 22 extension of SSH

SFTP port 22 , FTPS port 989 990
TFTP Trivial File Transfer Protocol : Port 69 UDP

Email Protocols : IMAP or POP

IMAP4 : POP 3
IMAP4 multiple access per client
POP 3 allows you to download locally and read them from the server. (It will remove it.)
SMTP Is the sending email



Firewall : Blocks unwanted traffic from the internet and your network

Host Based Firewall (Running directly on a host)
Network-Based Firewalls : Seperate internal network firewalls.
Border Firewall : Right on the edge of the network that is a blockade against the internet. (Explicitly allows traffic in.) You can also deny your users from reaching out.

New Firewall : WAF Web Application Firewall
Protects web servers from web application attacks (cross site scripting or SQL injection)

Generations First : Packet Filtering, Second : Stateful INspection : Third Generation Application-level firewalls WAF next generation - multiple capabilities into a single firewall. 

DMZ : Demilitarized Zone : Protects the internal structure. Anything that we want to have internal not to have any possibility of connecting to the internet or the network.

What is inside the DMZ : Everything that will have any internet connection to it.

Proxy Server : Like a firewall, sits inside a company. It's main job is to allow and deny internal computers connecting to certain external sites.

All in one UTM Unified Threat Management Firewall (It's a firewall, antivirus, Proxy Server, DMZ, etc) it's the "Final Solution" built into one.
