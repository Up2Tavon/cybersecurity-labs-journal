## Date
June 25, 2026

## Goal
Capture safe traffic from my own computer and identify basic protocols.

## Tool Used
Wireshark

## Websites Visited
- google.com
- chatgpt.com
- coursera.org
- docs.google.com

## Filters Tried
- dns
- tcp
- tls
- http

## What I Observed

### DNS
I saw: 
- Different websites
- Websites that I didnt open, Maybe they have something to do with my extensions
- Some websites looked like malware, but I did research and found out that its because of my adblocker extension or other sketchy extensions I have, but not malware more of adware
- A website called cdn.giveaway.com - This is adware, and I don’t have this extension, but another extension might be using its code or something
- I didn’t see coursea.org, even though it was opened. Do I have to actual click on the tab or open up another tab for it to be logged?
- I saw something called www.gstatic.com, and apparently its a domain operate by google. It function as a Content Delivery Network (CDN) designed to store and serve “static” web files—assets like images, CSS stylesheets, JavaScript libraries, and fonts
- It shows the standard query and if its a response or some weird hexa code like “0x8e46””

### TCP
I saw:
- A lot of different colors some were alarming, but idk what any of them mean really
	– Colors like: dark grey, light purple, dark blue, light pastel green, dark blue with red text, and red
- The info column has like 3 different categories:
	– Application data
	– [ACK] with sequence numbers, ack numbers, win numbers, and len numbers
	– [TCP …]
- TCP stands for Transmission Control Protocol
- Seeing a weird HTTP site called “HTTP/XML”

### TLS / HTTPS
I saw:
- A lot of secure applications or sites because compared to http there was barley anything in that search, so that shows how much we evolved with putting out HTTPS as new guideline.
- Learned about QUIC I was lowkey scared and thought someone was secretly data mining my PC because of the crypto thing it says in info column
- TLSv1.2 and TLSv1.3

### HTTP
I saw:
- Only 10 entries popped up
- The protocol is HTTP/XML
- 5 of them have protocol of 110, and the other half has protocol of 1011

## One IP Address I Noticed
- Source and Destination
IP: 192.168.1.162

## What I Think Happened
My computer used DNS to find the IP address of websites, then used TCP/TLS to connect securely.

## Questions I Still Have
- Why is HTTP/XML showing up?
- What are the rest of those unfamiliar sites that dns captured?
- Are the extensions safe or is there hidden malware?
- Why didn’t coursera or tabs I already had opened didn’t get picked up in the capture?
