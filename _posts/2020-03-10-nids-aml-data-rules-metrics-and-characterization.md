---
layout: post
title: "NIDS-AML Data Metrics Rules and Characterizations"
date: 2020-03-10
---

# Baseline Data Metrics

Name                     | Size(Gb) | # Unique Hosts |  # Pkts  | # Unique Flows | Avg pps
-------------------------|----------|----------------|----------|----------------|--------------
042219_1000.pcapng | 7 | | 7841380 | |
042319_1000.pcapng | 8 | | | |
042419_1000.pcapng | 7 | | | |
last_baseline_102519.pcapng | 9 | | | |





# Malicious Data Metrics


## Human-Generated Samples
Human-generated samples are generated from a Kali instance from `10.10.10.*`.

### Surfing Characterizations

### Attack Characterizations


# Baseline Data Rules
None, they all contain only benign samples

# Malicious Data Rules

Filename           | Attack              | Rules                | Why                         | Flow    | Notebook
------------------ | ------------------- | -------------------- | --------------------------- | ------- | ---------
052419_1504.pcapng | Nmap 192.168.1.0/24 | IP Src = 10.10.10.13 | Nmap uses ICMP TCP SYN scan |  |   
052419_1613.pcapng | Dig ds.lab | IP Src = 10.10.10.13 | Dig sends 2 packets via DNS |  |
052419_1618.pcapng | Dnsmap ds.lab -w /usr/share/wordlist/dnsmap.txt | IP Src = 10.10.10.13 | All traffic bw 192.168.1.7 (DC) and 10.10.10.13
 | |
052419_1623.pcapng | Dnswalk -r -d ds.lab | IP Src = 10.10.10.13 | All traffic bw 192.168.1.7 (DC) and 10.10.10.13
 | |
052419_1625.pcapng | dnstracer -r 3 -v  ds.lab | IP Src = 10.10.10.13 | Capture is so small that all traffic from 10.10.10.13 is malicious | |
052419_1627.pcapng | nslookup ds.lab | |  | |
052419_1629.pcapng | nslookup -type=ns  ds.lab | |  | |
052419_1631.pcapng | nslookup -type=soa ds.lab  and nslookup -query=mx  ds.lab | |  | |
060319_1510.pcapng | DVWA Pentesting | |  | |
060419_1255.pcapng | DVWA Pentesting | |  | |
060419_1413.pcapng | DVWA Pentesting | |  | |
060419_1509.pcapng | DVWA Pentesting | |  | |
060519_1319.pcapng | DVWA Pentesting | |  | |
060519_1355.pcapng | DVWA Pentesting | |  | |
060519_1420.pcapng | DVWA Pentesting | |  | |
060519_1434.pcapng | DVWA Pentesting | |  | |
070319_1422.pcapng | Yersinia GUI; DHCP attack | |  | |
070319_1502.pcapng | Yersinia GUI; DHCP attack | |  | |
071119_1521.pcapng | Yersinia stp -attack 3 -source 66:66:66:66:66:66 | |  | |
071119_1553.pcapng | Arpspoof -I eth0 -t 192.168.1.109 192.168.1.34 | |  | |
071119_1537.pcapng | Yersinia Interface: Yersinia -I  --> DHCP Dynamic Host Configuration Protocol | |  | |  
071119_1542.pcapng | Yersinia Interface: Yersinia -I --> DHCP Dynamic Host Configuration Protocol | |  | |
071119_1532.pcapng | Ettercap -Tqi eth0 -m ARP  | |  | |
071219_1324.pcapng | Bonesi -p TCP -r 1000 -I 50k-bots -u /site.html -d eth0 192.168.1.117:80 | |  | |
071219_1317.pcapng | Bonesi -p UDP -s 1200 -r 2 -i 50k-bots 192.168.1.117:2450 | |  | |
071219_1331.pcapng | Bonesi -i TCP -i 50k-bots -d eth0 192.168.1.117:80 | |  | |
071219_1342.pcapng | Kickthemout tool: Sudo python3 kickthemout.py -target 192.168.1.10 | |  | |
071219_1352.pcapng | Kickthemout tool: Sudo python3 kickthemout.py -t 192.168.1.5 -p 30 | |  | |  



# Human-Generated Data Rules
Filename           | IP of human host        
------------------ | --------------
P1_surfing_101619.pcap | 10.10.10.1
P1_dvwa_101619.pcap | 10.10.10.1
p2_surfing_101619.pcap | 10.10.10.2
P2_dvwa_102519.pcap | 10.10.10.2
p3_surfing_101619.pcap | 10.10.10.1
P3_dvwa_101619.pcap | 10.10.10.1
p4_surfing_101719.pcap | 10.10.10.1
P4_dvwa_101719.pcap | 10.10.10.1
p5_surfing_101719.pcap | 10.10.10.1
P5_dvwa_101719.pcap | 10.10.10.1
p6_surfing_101819.pcap | 10.10.10.1
P6_dvwa_101819.pcap | 10.10.10.1
p7_surfing_101819.pcap | 10.10.10.1
P7_dvwa_101819.pcap | 10.10.10.1
p8_surfing_101819.pcap | 10.10.10.1
P8_dvwa_101819.pcap | 10.10.10.1
p9_surfing_101819.pcap | 10.10.10.1
P9_dvwa_101819.pcap | 10.10.10.1
p10_surfing_102319.pcap | 10.10.10.2
P10_dvwa_102319.pcap | 10.10.10.2

To make these into queen files all surfing and all dvwa samples were combined
into separate files and labeled.

Since 'surfing' is considered to be benign traffic, that pcap is all labeled 0 (benign)
