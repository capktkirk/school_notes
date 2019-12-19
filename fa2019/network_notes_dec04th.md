Networking :

  Internet Security :
    Integrity       : -> Key is a hash, and you need a way to secure the hash.
                    Diffie-Hellman Key Exchange :
                      * Use the hash to ensure the data has not been altered.
                        * MD5 is used to do a hash sum on something to make sure it is the same as when it was sent.
                        * HMAC -> Hash Based Method Authentication
                          Sender -> HASH with a Key to generate a message (Message Authentication Code) are sent.
                          Receiver -> Decrypts the message and you check the hash.

                          Easy to use with the key, but getting the keys to both parties is hard.

                          Sender and receiver generate the *same* key.
                          Party A has a private key of : 5
                          Party B has a private key of : 4
                          Perform a similar mathematic action : 6^5 mod 13 and 6^4th mod 13 -> send the data to each other and undo the operation (9^5th mod 13, and 2^4 mod 13) and the result is 3 both times. This is a way to check if the data has been altered.


    Confidentiality : -> Asymetric Key and Symetric Key (Public/Private, One Key)
    Authentication  :
                      Are you who you say you are?
                      Basic Idea : There is some third party that provides a certificate validating you are who you are.
                      Certificate Authorities hold the certificate data to be checked against.
                      Layers of Certificate Authorities :
                      End=Entity Certificate -> Intermediate Certificate -> Root
                      Chain of Trust
                      Signing Chain

There is a push to put the Certificate into the DNS server resolution.

DNS -> Domain Name Service : How you take a website name and turn it into an IP address.
      DNS is already maintaining a list of who to go to and how to get there, why not add the certificate process?
      DNS-Security is what it would be adopted under. Reduce or eliminate the need for certificate authorities.



    Structured Cache System
      www.google.com
      ------------^ : Read right to left. .com is the highest domain.
                          Root
                           |
                         / | \
                        /  |  \
                       /   |   \
                    .org  .com  .net
    And before that in the www.google.com there are further drilling down of information.
    Root Server
    Name Server
    Local Server

    Going to do something like this in lab.
