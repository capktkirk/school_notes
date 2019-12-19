ping : 	RTT -> Round Trip Time
	Ping -> latency
	Traceroute -> able to trace the route it came across.
	wireshark -> allows us to examine the contents of packets.
		* Careful with CL wireshark. Doesn't always work.
	iperf -> PC1 	  <---->   PC2
		 client   <---->   server
		 ip	 <switch>  (for throughput)

last monday : store and forward with hops. Sometimes we will have an intermediary device
	      that stores data or routes it. A device like a switch. It will get the packet
	      waits until it gets the entire packet and then forward it along.
	example : (A) -(L)-> (hop) -(L)-> (hop) -(L)-> (B)
		: each hop (s) is an added delay.
		: P 	     = (p)ropagation delay
		: R          = (r)ate (transfer over time)
		: D          = (d)ata
		: (L)atency  = D/R + P
		: (L)(tot)   = 3 (L) + 2(hop)
		: (T)hruput  = D/L
		: RTT        = 2(L(tot))

	example 2 : 
	: (A) ---> (S) ---> (B) |______START_____|
	: R  = 			|
	: P  = 			|
	: SF = 			|
	: D  = n		|
	: (L) 	= D/R + P + S&F	|
	:			|

	: with two packets, the first packet will start sending with store and forward before
	: the second package finishes so that the second+ hops have less latency than the first one.

