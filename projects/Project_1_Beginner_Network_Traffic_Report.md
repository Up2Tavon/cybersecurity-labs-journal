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
	– 
- IP addresses being returned:
	– 
- Anything surprising:
	– 

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

- 

If I did not see much HTTP traffic, that is likely because most websites now use HTTPS instead of unencrypted HTTP.

## Interesting IP Addresses or Domains

| Domain or IP | What I think it was related to |
|---|---|
|  |  |
|  |  |
|  |  |

## What I Learned

In this lab, I learned that my computer communicates with many remote systems in the background. DNS helps find IP addresses, TCP helps create connections, and HTTPS/TLS protects web traffic through encryption.

## Questions I Still Have

- 
- 
- 

## Conclusion

This project helped me understand how basic network traffic appears in Wireshark. I practiced filtering packets, identifying common protocols, and documenting what I observed like a beginner security analyst.
