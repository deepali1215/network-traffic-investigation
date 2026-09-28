# Network Traffic Investigation

## Overview

A beginner cybersecurity project focused on analyzing captured network traffic using Wireshark from the perspective of a junior SOC analyst.

The investigation examined DNS requests and responses, TCP connections, and TLS-encrypted communication to understand how a local host communicated with remote systems.

## Scenario

A user reported that their computer was behaving strangely while accessing websites.

The objective was to investigate the network activity and determine whether the captured traffic provided evidence of suspicious behavior.

## Tools & Technologies

- Wireshark
- DNS
- TCP/IP
- TCP
- TLS 1.2
- Network packet analysis

## Investigation

### 1. DNS Analysis

Investigated DNS traffic using the Wireshark display filter:

`dns`

Observed a DNS query from the local host:

`192.168.0.109 → 192.168.0.1`

The query requested the IPv4 address of:

`ogs.google.com`

The corresponding response used transaction ID `0x3e69` and returned multiple IPv4 addresses along with a CNAME record.

### 2. TLS Analysis

Investigated TCP port 443 traffic using:

`tcp.port == 443`

One observed connection involved:

`192.168.0.109 ↔ 172.64.148.235`

Wireshark identified the communication as TLS 1.2 Application Data.

The TCP stream contained encrypted application data, demonstrating that the communication could be observed at the network level but its application content could not be read from the capture.

### 3. Evidence Correlation

The capture was searched for a DNS record connecting `172.64.148.235` to a domain.

No corresponding DNS mapping was observed within the captured traffic.

Rather than assuming the IP address was malicious, it was documented as an observed remote endpoint because the available evidence did not establish a malicious association.

## Findings

- Identified the local host involved in the investigation.
- Analyzed DNS query and response traffic.
- Correlated DNS requests using transaction IDs.
- Identified multiple returned IP addresses.
- Investigated TLS 1.2 communication over TCP port 443.
- Examined an individual TCP conversation using Follow TCP Stream.
- Practiced evidence-based analysis without assuming that encrypted or unfamiliar traffic was malicious.

## Conclusion

The investigation demonstrated a basic SOC workflow for network traffic analysis:

**Capture → Filter → Investigate → Correlate → Document**

The captured traffic showed DNS resolution and encrypted TLS communication. The available evidence did not provide sufficient information to classify the observed traffic as malicious.

## Skills Demonstrated

- Wireshark
- Network traffic analysis
- DNS analysis
- TCP/IP fundamentals
- TCP/TLS analysis
- Packet filtering
- Evidence correlation
- SOC investigation methodology
- Security documentation
