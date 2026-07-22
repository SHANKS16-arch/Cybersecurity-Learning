# Findings

## Capture Details

**Date:** 21 July 2026

**Interface Used:** enp0s3

**Targeted  Website:** https://google.com


## DNS Analysis

### DNS Request

A DNS request was observed when the browser attempted to access the website. The request asked the DNS server to resolve the domain name **googlee.com** into its corresponding IP address.

 DNS Request Packet: 1
 DNS Response Packet: 2

### DNS Response

The DNS server responded with the IP address associated with **google.com**. After receiving the response, the browser was able to identify the destination server and continue the connection process.



## TCP Three-Way Handshake

A TCP three-way handshake was observed before any web data was exchanged.

The handshake packets consisted of:

- SYN: 8
- SYN-ACK: 10
- ACK: 11

This process established a reliable connection between the client and the server and confirmed that both devices were ready to communicate.

---

## TLS Handshake

After the TCP connection was established, a TLS handshake was performed.

The purpose of the TLS handshake was to establish a secure encrypted connection between the client and the server. TLS also verifies the identity of the server using digital certificates before encrypted communication begins.


 First TLS Packet: 12
 TLS Version Observed: TLS 1.2

## Communication Flow

The communication process occurred in the following order:

1. The user entered **https://google.com** in the browser.
2. The browser sent a DNS request to obtain the IP address of the website.
3. The DNS server returned the corresponding IP address.
4. A TCP three-way handshake established a reliable connection.
5. A TLS handshake created a secure encrypted connection.
6. HTTPS was used to securely exchange data.
7. The webpage was successfully displayed in the browser.



## Conclusion

This investigation demonstrated the complete process of establishing a secure web connection. DNS resolved the domain name into an IP address, TCP established a reliable connection, TLS encrypted the communication, and HTTPS securely transferred the webpage data. Capturing these packets using Wireshark provided a practical understanding of how browsers communicate securely with web servers.
