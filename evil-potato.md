# Evil Potato Challenge Documentation

## Overview

The "evil-potato" challenge involves analyzing a packet capture (pcap) file to identify and understand an attack. This documentation describes the steps taken to analyze the pcap file and the findings from the analysis.

## Tools Used

- **Wireshark**: A network protocol analyzer used to capture and interactively browse network traffic.

## Steps for Analysis

1. **Open the pcap file**:
    - Launch Wireshark.
    - Open the provided pcap file named `evil_potato.pcapng`.

2. **Filter the Traffic**:
    - Apply the filter `http` to focus on HTTP traffic.

3. **Examine the Packets**:
    - The filtered traffic shows several packets exchanged between `192.168.228.128` and `172.217.168.68`.
    - Notable packets include:
        - Packet 6092: SYN packet initiating the connection.
        - Packet 6093: SYN-ACK response from the server.
        - Packet 6094: ACK packet completing the TCP handshake.
        - Packet 6095: HTTP GET request to `http://www.google.com/search?q=shc2023%7Bdel3te_the_brows3r_hist0ry_before_i_di3%7D`.
        - Packet 6096: HTTP 302 Found response redirecting to a different URL.

4. **Analyze HTTP Request**:
    - The HTTP GET request in packet 6095 contains the query string: `shc2023{del3te_the_brows3r_hist0ry_before_i_di3}`.
    - This suggests the attack involves a malicious search query possibly part of a CTF challenge.

5. **Inspect the HTTP Response**:
    - The HTTP 302 Found response in packet 6096 redirects the client to `https://www.google.com/search?q=shc2023%7Bdel3te_the_brows3r_hist0ry_before_i_di3%7D`.
    - This indicates the request was processed and redirected by the server.

## Conclusion

The captured traffic indicates an HTTP GET request was made with a potentially malicious query string related to deleting browser history. The server responded with a 302 Found status, redirecting the request to another URL. This analysis provides insight into the nature of the attack and the steps involved in investigating it using Wireshark.

## References

- [Wireshark User Guide](https://www.wireshark.org/docs/wsug_html_chunked/)
- [Evil Potato Challenge](https://library.m0unt41n.ch/challenges/evil-potato)