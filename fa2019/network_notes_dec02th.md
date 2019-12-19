[Programs](Programs) :

Before all ACK's went through, now ACK has a potential for dropping.

Modify the code, change send to packetErrorSend (for the ack.)

select on the client side potentially. (use select to wait for the ack return, and if the ack doesn't get returned, resend.)


Today : HTTP
Wed : Net Security
Monday : DNS
Wed : Review


http : it is used to send html documents/update/fetch. Hyper Text Transfer Protocol

Format of GET requests.

\r\n (carriage return, new line)

pressing the enter key sends \r\n in telnet

URI is who you're going to
Version is HTTP/1.1 (there are various versions

Request line is METHOD URI VERSION \r\n

First thing you get back is a "Result"


Caching HTTP :
  Making things faster (don't have to redownload same content)
  cookies and etags
  cache directives (specify when transfering data whether or not it can be cahced)
    You can specify how long to cache for as well.

#HTTP Versions
  HTTP uses TCP
  Multiple versions : 1.0, 1.1, 2.0, 3.0
  Big differences between 1.0 and 1.1 :
    1.1 :
      introduces persistent connection
        1.0 : closes after last byte of data is sent.


Request Pipelining :
  Send multiple requests to a server without waiting for a response (1.0 send request, wait for response.)

Byte Serving : 1.0 : You get the whole file or none of the file. 
              1.1 : specifiy chunks of the file to get back.

  1.1 allows for virtual servers. You can host multiple webpages on a single site.
  They also added on content encoding (you can compress the http data in order to improve the transfer speed)

In lab we'll get to look at some of these features and some of the other changes made between 1.0 and 1.1


Current Section 8.4.3
Next Section : 9.3.1

DNS

Domain Name Server

One of the basic levels of network security is TLS : Transport Layer Security

TLS was created to replace SSL

Basic overview of TLS : 
  At Website : Shopping : Going to use credit card
    The goal of TLS is to provide a secure section, for data we don't want to be sharing.
    * Card Number, Address, Amount, Shipping Data
      We need this data to be both private and secure.
      Cannot be viewed or modified.
      Verification of who we are talking to.
      Confidentiality(Hidden), Integrity(Private), Authentication(Verified)

      TLS sits between the HTTP and TCP.

      TLS doesn't change anything between HTTP and TCP, it just takes in and spits out secure code.

      At run time a pair of TLS participants negotiate on which cryptography to use :
        * Symetric-Key
        * Public Key
        * Data Integrity

      TLS will need about 6 keys
        * One incoming
        * One outgoing
        * Two for initialization
      Hash of setup is exchanged to ensure setup integrity


  Confidentiality : Keying System :
    Symetric-Key :
      One key that both parties have a copy of. Use the key to lock and unlock the data. Trick is getting both parties in posession of the key. Sharing the key exposes the data


  Public-Key : (Asymetric Key) You have a public key, anyone can get ahold of the public key.
  What you keep hidden is a private key : This is the public-private key pairing.



How do I make sure it hasn't been modified (How to detect the change : Source/Data integrity)

  We have encrypted data, we send something that is a backup, if the two files don'trelate to each other then we know something has changed. We use HASH : And encrypting hash is very similar to the private/public key.
