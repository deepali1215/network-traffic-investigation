# Network Traffic Investigation

## Overview

A beginner cybersecurity project focused on analyzing captured network traffic using Wireshark from the perspective of a junior SOC analyst.

The investigation examined DNS requests and responses, TCP communication over port 443, and TLS-encrypted application traffic to understand how a local host communicated with remote systems.

## Scenario

A user reported that their computer was behaving strangely while accessing websites.

The objective was to investigate the captured network activity, understand the communication flow, and identify observations that could require further investigation without automatically classifying unfamiliar traffic as malicious.

## Tools & Technologies

* Wireshark
* DNS
* TCP/IP
* TCP
* TLS 1.3
* Network packet analysis

## Investigation

### 1. DNS Analysis

DNS traffic was investigated using the Wireshark display filter:

`dns`

A DNS query was observed from the local host:

`192.168.0.109 → 192.168.0.1`

One observed query requested information for:

`ogads-pa.clients6.google.com`

The corresponding DNS response returned the IPv4 address:

`172.217.161.10`

This demonstrated the process of DNS resolution, where a host queries a DNS server to obtain an IP address associated with a domain.

### 2. TCP Analysis

TCP traffic using destination port 443 was investigated with the filter:

`tcp.port == 443`

An observed connection involved:

`192.168.0.109 → 142.251.106.94`

The traffic used destination port `443`, which is commonly associated with HTTPS communication.

A TCP packet was examined to understand the communication between the local host and the remote endpoint.

### 3. TLS Analysis

TLS traffic was investigated using the Wireshark display filter:

`tls`

Wireshark identified application traffic as:

`TLSv1.3 — Application Data`

The communication between the local host and the remote endpoint was encrypted using TLS 1.3.

The packet capture allowed observation of network-level information such as IP addresses, ports, protocols, and packet metadata, while the actual application content remained encrypted and was not directly readable from the capture.

### 4. Evidence Correlation

The investigation followed the communication flow from DNS resolution to TCP communication and TLS-encrypted traffic.

The analysis documented what was directly observable in the packet capture rather than assuming that the traffic was malicious or completely safe.

## Findings

* Identified the local host involved in the investigation: `192.168.0.109`.
* Observed DNS communication between the local host and DNS server `192.168.0.1`.
* Identified a DNS query for `ogads-pa.clients6.google.com`.
* Observed the DNS response returning `172.217.161.10`.
* Identified TCP communication involving destination port `443`.
* Observed communication with remote endpoint `142.251.106.94`.
* Identified TLS 1.3 application data.
* Observed that the application content was encrypted and not directly readable from the capture.
* Practiced evidence-based analysis without automatically treating unfamiliar or encrypted traffic as malicious.

## Conclusion

The investigation demonstrated a basic network traffic analysis workflow:

**Capture → Filter → Investigate → Correlate → Document**

The captured traffic showed DNS resolution followed by TCP communication over port 443 and TLS 1.3 encrypted application traffic.

The available packet evidence was sufficient to describe the communication flow, but it was not sufficient on its own to classify the observed traffic as malicious.

## Skills Demonstrated

* Wireshark
* Network traffic analysis
* DNS analysis
* TCP/IP fundamentals
* TCP/TLS analysis
* Packet filtering
* Evidence correlation
* SOC investigation methodology
* Security documentation
