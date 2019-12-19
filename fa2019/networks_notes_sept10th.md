Layer 2 (Link Layer)
  - Frames (Packets)
  - Ethernet
    + Payload : | preamble | header | payload |
    preamble is sync data (clock data sync)
    pre-amble and header are fixed sizes.
    payload is going to change.
    header and preamble eats good put

    header in an ethernet packet starts with the MAC address.
    ethernet is flat (no heirarchy)
    
  Destination (Mac address) (6 bytes long)
  Source (Mac address) (6 bytes long)
  Type or Length (2 Bytes, tells you type or length of packet)
  IEEE -> decided the packet would say length instead of type.

  type or length field performs doubel duty :
    0x0000 -> 0x07ff -> Length
    0x0800 -> 0xffff -> type

  payload being sent.
  On the end there could be a CRC (error correcting code)


    | preamble | type length | header | payload | CRC |
    Max length is going to be 1500 Bytes, larger than that and you end up with a second packet.
  

  Error Sources :
  
