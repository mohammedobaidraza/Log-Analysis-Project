# Network Protocol Analysis with PCAP and SNORT

This repository contains a detailed analysis of network protocols using a captured PCAP file and SNORT IDS/IPS. The project aims to analyze network traffic, detect anomalies, and identify potential malicious activities based on the traffic patterns.

## Table of Contents
- [Overview](#overview)
- [Key Protocols Observed](#key-protocols-observed)
- [Alerts Detected](#alerts-detected)
- [Tools Used](#tools-used)
- [PCAP File Analysis](#pcap-file-analysis)
- [SNORT Configuration](#snort-configuration)
- [Conclusion](#conclusion)
- [References](#references)
  
### Overview
This project analyzes a PCAP file captured from a home network environment. The traffic consists of various protocols, including TCP, UDP, QUIC, DNS, and TLS. The analysis was performed using **Wireshark** for packet analysis and **SNORT** for intrusion detection.

The traffic was captured over 38 minutes, resulting in a file size of 362MB and a total of 344,618 packets.

#### Key Protocols Observed
1. **TCP** - 84.83% of the packets, responsible for most of the communication.
2. **UDP** - 13.10% of the packets, used primarily for DNS and QUIC.
3. **QUIC IETF** - 12.81% of the packets, modern protocol built over UDP for web services.
4. **DNS** - 0.21% of the packets, responsible for domain-to-IP address translation.
5. **TLS** - 16.62% of the packets, responsible for secure communications (HTTPS).

#### Alerts Detected
SNORT detected **31,965 alerts** during the analysis, with significant activity involving:
- **HTTPS traffic**: Possible encrypted communications or attempts to hide malicious behavior.
- **HTTP traffic**: Detection of standard web traffic, requiring further inspection.
- **ICMP traffic**: A small amount of traffic, often used for network diagnostics.

#### Tools Used
- **Wireshark**: For deep packet inspection and protocol analysis.
- **SNORT**: To detect potential malicious activity or abnormal patterns in the network traffic.
  
#### PCAP File Analysis
The PCAP file was analyzed using Wireshark. Below are the key observations:
- **DNS Queries**: Multiple queries related to Netflix, GitHub, and Google domains were identified.
- **HTTP Traffic**: Captured HTTP GET and POST requests with status codes, including 304 Not Modified.
- **ICMP Traffic**: Detected ICMP packets related to Mobile IP advertisements.

#### SNORT Configuration
The following local SNORT rules were used to detect potential threats:
```shell
alert icmp any any -> 127.0.0.0/24 any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
alert tcp any any -> 127.0.0.0/24 80 (msg:"HTTP access detected"; sid:1000002; rev:1;)
alert tcp any any -> 127.0.0.0/24 443 (msg:"HTTPS access detected"; sid:1000003; rev:1;)
```
### Conclusion
- This analysis has provided insights into the network traffic on the home network, revealing potential suspicious activities involving HTTPS and QUIC traffic. Further inspection with SNORT rules indicated alerts on both HTTP and HTTPS traffic, which should be investigated in more detail.

### References
- Roesch, M. (1999). SNORT - Lightweight Intrusion Detection for Networks. Retrieved from https://www.snort.org/
- Combs, G. (2024). Wireshark Network Protocol Analyzer. Retrieved from https://www.wireshark.org/

