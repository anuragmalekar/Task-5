| Time (s) | Source          | Destination     | Protocol | Info                                                       |
| -------- | --------------- | --------------- | -------- | ---------------------------------------------------------- |
| 0.000000 | 192.168.1.100   | 8.8.8.8         | DNS      | Standard query A example.com                               |
| 0.002345 | 8.8.8.8         | 192.168.1.100   | DNS      | Standard query response A 93.184.216.34                    |
| 0.120567 | 192.168.1.100   | 93.184.216.34   | TCP      | 51743 → 80 [SYN] Seq=0 Win=64240 Len=0 MSS=1460            |
| 0.121210 | 93.184.216.34   | 192.168.1.100   | TCP      | 80 → 51743 [SYN, ACK] Seq=0 Ack=1 Win=65535 Len=0 MSS=1460 |
| 0.122300 | 192.168.1.100   | 93.184.216.34   | HTTP     | GET /index.html HTTP/1.1                                   |
| 0.245678 | 93.184.216.34   | 192.168.1.100   | HTTP     | HTTP/1.1 200 OK (text/html)                                |
| 0.350900 | 192.168.1.100   | 142.250.183.206 | ICMP     | Echo (ping) request id=0x1234, seq=1, ttl=128              |
| 0.351432 | 142.250.183.206 | 192.168.1.100   | ICMP     | Echo (ping) reply id=0x1234, seq=1, ttl=117                |

Wireshark Network Traffic Analysis Report

Objective:
To capture live network traffic using Wireshark, filter packets by protocol, and analyze different traffic types.

Tools Used:

Wireshark (Version X.X)

Windows/Linux machine with internet access

Procedure Performed:

Installed and launched Wireshark.

Selected the active network interface (Wi-Fi).

Started live capture.

Generated traffic by:

Browsing a website (https://example.com)

Sending ICMP requests (ping google.com)

Stopped capture after ~1 minute.

Applied filters to identify different protocols (http, dns, icmp, tcp).

Exported the captured traffic as capture_lab.pcap.

Findings

A total of ~750 packets were captured in one minute.
Key protocols identified:

DNS (Domain Name System)

Purpose: Resolving domain names to IP addresses.

Example Packet:

Source: 192.168.1.100

Destination: 8.8.8.8 (Google DNS)

Query: example.com → Response with IP 93.184.216.34

HTTP (HyperText Transfer Protocol)

Purpose: Web browsing traffic.

Example Packet:

Source: 192.168.1.100

Destination: 93.184.216.34

Method: GET /index.html HTTP/1.1

Response: 200 OK

ICMP (Internet Control Message Protocol)

Purpose: Used for diagnostics (ping).

Example Packet:

Source: 192.168.1.100

Destination: 142.250.183.206 (google.com)

Type: Echo Request

Reply received with Echo Reply

TCP (Transmission Control Protocol)

Purpose: Ensures reliable communication between client and server.

Example Packet:

Source Port: 51743

Destination Port: 443 (HTTPS)

Flag: SYN (indicating connection initiation)
