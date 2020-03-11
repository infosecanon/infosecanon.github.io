---
layout: post
title: "NIDS-AML Data Metrics Rules and Characterizations"
date: 2020-03-10
---

# Baseline Data Metrics

Name                     | Size(Gb) | # Unique Hosts |  # pkts  | # unique flows | avg pps |
--------------------------------------------------------------------------------
042219_1000.pcapng | 7 | | 7841380 |
042319_1000.pcapng | 8 | | |
042419_1000.pcapng | 7 | | |
last_baseline_102519.pcapng | 9 | | |





# Malicious Data Metrics
Name                     | Size(Gb) | # Unique Hosts |  # pkts  | # unique flows
--------------------------------------------------------------------------------
052419_1504.pcapng | | | |
052419_1613.pcapng | | | |
052419_1618.pcapng | | | |
052419_1623.pcapng | | | |
052419_1625.pcapng | | | |
052419_1627.pcapng | | | |
052419_1629.pcapng | | | |
052419_1631.pcapng | | | |
060319_1510.pcapng | | | |
060419_1255.pcapng | | | |
060419_1413.pcapng | | | |
060419_1509.pcapng | | | |
060519_1319.pcapng | | | |
060519_1355.pcapng | | | |
060519_1420.pcapng | | | |
060519_1434.pcapng | | | |
070319_1422.pcapng | | | |
070319_1502.pcapng | | | |
071119_1521.pcapng | | | |
071119_1553.pcapng | | | |
071119_1537.pcapng | | | |
071119_1542.pcapng | | | |
071119_1532.pcapng | | | |
071219_1324.pcapng | | | |
071219_1317.pcapng | | | |
071219_1331.pcapng | | | |
071219_1342.pcapng | | | |
071219_1352.pcapng | | | |

## Human-Generated Samples


### Surfing

### Attack


# Baseline Data Rules
None, they all contain only benign samples

# Malicious Data Rules
Name                   |  Attack  |  Rules                        | Why    |  Attack Chain  
-------------------------------------------------------------------------------------------
052419_1504.pcapng | Nmap 192.168.1.0/24 | X[((X.sa == '10.10.10.13') & (X.pr == 1.0)) | ((X.sa == '10.10.10.13') & (X.pr == 6.0))] | Nmap uses ICMP
TCP SYN scan |
052419_1613.pcapng | Dig ds.lab | X[((X.sa == '10.10.10.13') & (X.dp == 53.0))] | Dig sends 2 packets via DNS |
052419_1618.pcapng | 052419_1618.pcapng | Dnsmap ds.lab -w /usr/share/wordlist/dnsmap.txt |  X[((X.da == '10.10.10.13') & (X.sp == 53.0))] | All of the traffic occurs between 192.168.1.7 (DC) and 10.10.10.13
052419_1623.pcapng | Dnswalk -r -d ds.lab | X[((X.da == '10.10.10.13') & (X.sp == 53.0))] | All of the traffic occurs between 192.168.1.7 (DC) and 10.10.10.13 |
052419_1625.pcapng | dnstracer -r 3 -v  ds.lab | X[((X.da == '10.10.10.13') | (X.sa == '10.10.10.13'))] | The capture is so small that all 10.10.10.13 traffic is malicious |
052419_1627.pcapng | | | |
052419_1629.pcapng | | | |
052419_1631.pcapng | | | |
060319_1510.pcapng | | | |
060419_1255.pcapng | | | |
060419_1413.pcapng | | | |
060419_1509.pcapng | | | |
060519_1319.pcapng | | | |
060519_1355.pcapng | | | |
060519_1420.pcapng | | | |
060519_1434.pcapng | | | |
070319_1422.pcapng | | | |
070319_1502.pcapng | | | |
071119_1521.pcapng | | | |
071119_1553.pcapng | | | |
071119_1537.pcapng | | | |
071119_1542.pcapng | | | |
071119_1532.pcapng | | | |
071219_1324.pcapng | | | |
071219_1317.pcapng | | | |
071219_1331.pcapng | | | |
071219_1342.pcapng | | | |
071219_1352.pcapng | | | |



# Human-Generated Data Rules
