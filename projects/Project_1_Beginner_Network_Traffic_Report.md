## Project Goal

The goal of this project was to capture safe network traffic from my own computer and identify basic protocols such as DNS, TCP, HTTP, and HTTPS/TLS.

## Tools Used

- Wireshark
- Chrome web browser
- My own safe network traffic

## Websites Visited

- google.com
- youtube.com
- spotify.com
- twitch.com
- wordle.com
- netflix.com

## Filters Used in Wireshark

- dns
- tcp
- tls
- tcp.port == 443
- tcp.port == 80
- udp.port == 53

## What DNS Does

DNS stands for Domain Name System. It helps turn website names, like google.com, into IP addresses that computers can use to communicate.

## What I Observed with DNS

I used the `dns` filter in Wireshark and observed:

- Domain names being requested:
  - wpad.lan
  - clientservices.googleapis.com
  - www.gstatic.com
  - oauthaccountmanager.googleapis.com
  - www.google.com
  - accounts.google.com

- DNS communication observed:
  - My computer appeared to send DNS queries from an IPv6 address on my network.
  - The destination `2603:8002:7df0:6e30::1` appeared often in DNS traffic, which may be my router, gateway, or DNS resolver.
  - I saw DNS activity before manually opening Google, likely because Chrome, Google services, or background applications were already communicating.

- Anything surprising:
  - I was surprised by how many background services appeared before I even opened a website.
  - When I opened Google, I saw related services such as Google accounts, static content, and client services. This showed me that visiting one website can involve multiple domains and background connections.

## What TCP Does

TCP stands for Transmission Control Protocol. It helps create a reliable connection between my computer and another system.

## What I Observed with TCP

I used the `tcp` filter in Wireshark and observed:

- Many packets between my computer and remote IP addresses
- Source and destination ports
- Repeated communication between my device and websites/services

## What HTTPS/TLS Does

HTTPS is the secure version of HTTP. TLS helps encrypt web traffic so that the data being sent between my browser and websites is protected.

## What I Observed with HTTPS/TLS

I used the `tls` and `tcp.port == 443` filters and observed:

- Most modern web traffic used port 443
- Website traffic was encrypted
- I could see connection information, but not the actual private content being sent

## What I Observed with HTTP

I used the `tcp.port == 80` filter and observed:

- I saw around 10 entries using port 80.
- I was surprised to see HTTP traffic because I did not intentionally visit any unencrypted HTTP websites.
- One HTTP entry included `/we1/uCglcmwwftc.crl HTTP/1.1`.

This may have been related to a certificate revocation list, also known as a CRL. Certificate checks can happen in the background when browsers or applications verify whether a certificate is still trusted. Even though most websites use HTTPS, some background certificate-checking traffic may still appear over HTTP.
## Interesting IP Addresses or Domains

| Domain or IP | What I think it was related to |
|---|---|
| 2603:8002:7df0:6e30::1 | This appeared often as the destination for DNS traffic. I think it may be my router, gateway, or DNS resolver. |
| 2603:8002:7df0:6e30:e473:175d:d25:c3e8 | This appeared as the source address in DNS traffic. I think this may be my computer’s IPv6 address on my local network. |
| /we1/uCglcmwwftc.crl HTTP/1.1 | This looked like a certificate revocation list request. It may be related to background certificate/trust checking. |
| clientservices.googleapis.com | This appears related to Google/Chrome background services. |
| www.gstatic.com | This appears related to Google static content such as scripts, images, or web resources. |
| accounts.google.com | This appears related to Google account login or authentication services. |
## What I Learned

In this lab, I learned that my computer communicates with many remote systems in the background. DNS helps find IP addresses, TCP helps create connections, and HTTPS/TLS protects web traffic through encryption.

## Questions I Still Have

- Why am I seeing IPv6 addresses? Does it have something to do with using an Ethernet cable?

Possible answer: I am likely seeing IPv6 because my network, ISP, router, and device support IPv6. This is normal on modern networks. It is probably not because I am using Ethernet specifically. Both Wi-Fi and Ethernet can use IPv4 or IPv6 depending on the network configuration.

## Skills Practiced

- Capturing safe network traffic
- Filtering packets in Wireshark
- Identifying DNS traffic
- Identifying TCP traffic
- Recognizing HTTPS/TLS traffic on port 443
- Noticing unexpected background network activity
- Documenting observations like a beginner security analyst

## Conclusion

This project helped me understand how basic network traffic appears in Wireshark. I practiced filtering packets, identifying common protocols, and documenting what I observed like a beginner security analyst.
