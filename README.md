# IDPI
An advanced extra higher speed deep packet inspect library/solution, with the private original AFDL language support, which make it possiable to generate/update ruleset conveniently and efficiently. We have tried to include solutions such as hyperscan dpdk to speed up the performance. 
It now support NFV and SDN framwork. It now already be used in vpp as a proven DPI solution.


+ **[Performance](#performance)**
+ **[Supported Architecture](#supported architecture)**
+ **[AFDL](#afdl)**
+ **[Contact Us](#contact-us)**

## Performance
The average packet length is 512 bytes, and the performance can reach 40Ge line speed in 60 million concurrent connections.

## Supported Architecture
Support Linux/Freebsd system, support X86,MIPS,ARM processing architecture.

## AFDL
AFDL(advance feature description language), which make it possiable to generate/update ruleset conveniently and efficiently. It can define regex/expression/state like C/C++ language syntax, also define the FSM dynamicly with a concisely syntax. 
The ruleset can be host independent generated and loaded.
example:
classifier MYTARGET {
	
    cfid = 10001;
	category = http;
	inherit = http;
	action = drop;

	regex a;
		a.pattern = where;
		a.range = [0-100];
		a.group = TCP;
	regex b;
		b.pattern = are;
		b.range = [10-1000];
		b.group = TCP;
	regex c;
		c.pattern = you;
		c.range = [0-1460];
		c.group = TCP;
	regex d;
	    d.pattern = now.*ok;
	    d.range = [0-1460];
	    d.group = TCP;
	
	rule r1 = b&c;
	rule r2 = a&(b|c);
	rule r3 = a;
	rule r4 = b;
	rule r5;
	r5 = (c|a)&b;
	
	state s1,s2,s3;
	
	jump initial -(r1)-> s1 -(r2)-> s2 -(r3)-> s3 -(r4)-> final ;
	jump                 s1      -(r5)->       s3               ;
	jump initial -(r5)-> final                                  ;
}
 
<img src="/screenshots/afdl.png" width="200px"> 
<img src="/screenshots/classifier.png" width="200px"> 
<img src="/screenshots/result.png" width="200px">

## Contact Us
Feel free to contact us for any support, query, suggestion or even say hi.
 + [aoac](mailto:ecoocn@outlook.com)
