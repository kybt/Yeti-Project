#Yeti Root Testbed Health Monitoring Proposal

0. introduction
------------

Yeti root testbed sometimes will get problems, such as network
failures, DSC page data missing, without response, data inconsistency 
and so on. So we need to detect the running status of Yeti root name 
servers. In this document we are propose what metrics to be monitored 
and how to conduct the monitoring work in Yeti testbed.
	
Brief outline:

    What metrics will be monitored: section 1-6
    How to do monitoring: section 7
    How to show the monitoring data: section 8

1. yeti  server network metrics: all yeti servers
------------
    1.1 ping6 dealy (??? daily?)
        check per an hour
    1.2 Hoplimit
        count IPv6 Hoplimit
        
2. Yeti Distribution Masters metrics
------------
    2.1 DM group
           BII,WIDE
    2.2 SOA serial number
        compare with other root name servers
    2.3 RTT
        dig query respone time
    2.4 NS records
    2.5 DNSKEY
        ZSK, KSK status
        
3. Yeti root name server metrics
------------
    3.1 SOA serial number
        compare with other root name servers
    3.2 RTT
        dig query response time
    3.3 NS records
    3.4 DNSKEY
        ZSK, KSK status
    3.5 Zone Transfer
         open or closed
 
4. Yeti recursive server metrics
------------
    4.1 RTT
    4.2 SOA
    4.3 DNSKEY
    4.4 root zone NS records

5. DSC/data collecting system
------------
    5.1 root server upload data or not
    
	
6. result format
------------
    use json to store monitoring result
	
	6.1 root server sample
	{
	"Name":"yeti-dns01.dnsworkshop.org.",
	"Status": "UP",
	"Ping6": "100ms",
	"RTT":	"295ms",
	"Serial": "2015072600",
	"NS": [
		{"Name":"bii.dns-lab.net.","IPV6":"240c:f:1:22::6"},
		{"Name":"yeti.bofh.priv.at.","IPV6":"2a01:4f8:161:6106:1::10"},
		{"Name":"yeti.ipv6.ernet.in.","IPV6":"2001:e30:1c1e:1::333"},
		{"Name":"dahu1.yeti.eu.org.","IPV6":"2001:4b98:dc2:45:216:3eff:fe4b:8c5b"},
		{"Name":"ns-yeti.bondis.org.","IPV6":"2a02:2810:0:405::250"},
		{"Name":"yeti-ns.ix.ru.","IPV6":"2001:6d0:6d06::53"},
		{"Name":"yeti-ns.tisf.net.","IPV6":"2001:559:8000::6"},
		{"Name":"yeti-ns.wide.ad.jp.","IPV6":"2001:200:1d9::35"},
		{"Name":"yeti-ns.as59715.net.","IPV6":"2a02:cdc5:9715:0:185:5:203:53"},
		{"Name":"yeti-dns01.dnsworkshop.org.","IPV6":"2001:1608:10:167:32e::53"}
	],
	"ZSK": [
		{"Algorithm":8,"Last section":"M8L51I/b"},
		{"Algorithm":8,"Last section":"ylQALn9x"}
	],
	"KSK": [
		{"Algorithm":8,"Last section":"ABX8sQmwO7s="}
	],
	"Zone transfer":"closed"
	}

7. How to monitoring
------------
    7.1 monitoring rate
	    per hour
		
8. How to show the monitoring result
------------
    8.1 display in official website
 	    yeti-dns.org
