DNS -> Domain Name Service
-> Tree Structure
  * Distributed over multiple servers
  * Root Server :
    * Maintains records of top level stuff (.com, .edu, .net, .org)
    * Maintained by an organization
    * Internet Corporation for Assigned Names and Numbers (ICANN for short)
    * Recursive searchtree from root

  * DNS Resolver : Local to You : Does the work to resolve a web address
  * Recursive Look up : Answer section automatically.
  * Non Recursive Look up : Have to perform it multiple times (dig)
  * Reverse DNS look up : (Starting IP Address will find the domain name
    for it.

Resoure Records of DNS :
  * Zones (How DNS is actually implemented)
    * Subtrees of the larger DNS concept
    * Typically divided up by top level domains
    * Name servers //How domain is accessed.
    * Maintained as a five-tuple : name, value, type, class, TTL
    * Name -> Record
    * Value
    * Type -> Tells you how to interpret the value field
      * Type and how it relates to the value field :
        * A     : IP Address Maping Record/DNS Host Record
        * NS    : Name Server Records : Domain name for a host that is running on a name server
                  Should know how to resolve more specific domain
        * MX    : Mail Exchanger record
        * PTR   : Reverse-lookup Pointer records
        * CNAME : Cannonical name for a particular host. Defines aliases for domain.
        * SOA   : Start of Authority Record : Beginning of a DNS zone file, and indicates the
                  Authoritive Name Server
    * Class -> How DNS name space is organized (Most common is IN, Chaos CH, Hesiod HS)
    * TTL -> How old the record is.

Registrars -> ICANN Open NIC (Network Information Center) Who you would go through to get your domain registered to an IP

Dynamic DNS -> Client Version : Most home/small businesses have an ID assigned by ISP
  Updates Record of your domain

Dynamic DNS : Updating name server or root records : Requires security to ensure records are updated correctly.

- DNS Security :
  - DNS Hijacking//DNS Redirection with malicious intent.
  - Two Common Goals :
    - Phishing : Steal your Data
    - Pharming : Get you to ads or malicious sites.
-> How to DNS Hijacking
  -> Local DNS :
    -> Malware on PC that changes local DNS Setting
    -> Possible at router level : Alter/Redirect any DNS query.
    -> Man in the middle attacks : Spoofing ID
    -> Hacking an actual DNS Server
  -> This has led us to DNS-Security :
    * DNS Sec -> Additiona layer of security -> More resource records, resolver goes through more steps before 
      returning results.
    * Added in more data into the Five-Tuple :
      * RRSIG   : Resource Recogrd Signatures : Cryptographic Signatures for a given record.
      * DNSKEY  : Holds a public-key that is used in a DNS Authentication Process. DiffieHulman Key Exchange.
      * DS      : Delegation Signer : A hashed fingerprint that you can check against for validity.

  DNS resolver takes more steps to ensure the security on the DNS server before it gives you a result to prevent malicious action.


