# Linux Network Basics

## Goal
Practicing how to use Linux to answer basic network question
## What I checked
- The IP address of the linux system
- The default route/gateway
- The connectivity to ip address 8.8.8.8
- The DNS resolution to domain google.com
## Commands I used
- ip addr
- ip route
- ping -c 4 8.8.8.8
- ping -c 4 google.com
- nslookup google.com
- dig google.com

## Independent Analysis Task
1. What IP address did your Linux system have?
	- 172.23.10.251
	- It had a IPv4 (inet) and IPv6 (inet6)
2. Which interface looked active?
	- The loopback and the broadcast looked active because of the status inside the “<>” saying “UP” and not “DOWN”
	- GPT Help: The active network interface was eth0 because it had my IPv4 address 172.23.10.251 and showed UP/LOWER_UP.
		- The active interface looked like eth0 because it had my IPv4 address and showed UP/LOWER_UP. The loopback interface was also UP, but loopback is only local to the machine.
3. What did the default route/gateway show?
	- Showed IPv4 address 172.23.0.1
	- "default via 172.23.0.1 dev eth0 proto kernel 172.23.0.0/20 dev eth0 proto kernel scope link src 172.23.10.251"
4. Did pinging 8.8.8.8 work?
	- Yes, 4 packets were transmitted and 4 were received
	- No packets were loss and the time it took was 3273ms
5. Did pinging google.com work?
	- Yes, 4 packets were transmitted and 4 were received
	- No packets were loss and the time it took was 3273ms
6. If 8.8.8.8 works but google.com fails, what might that suggest?
	- That might suggest that the IP address couldn't find the name to google
	- GPT Help: If ping 8.8.8.8 works but ping google.com fails, that suggests DNS may be broken because the network can reach IP addresses, but it cannot resolve domain names into IP addresses.
7. What looked normal?
	- The ethernet cable I’m using matching with what the ip addr saying that its on an eth0
8. What are you unsure about?
	- I’m unsure about what it means when 8.8.8.8 works, but google.com fails

## Analyst Challenge
Think through this scenario:
```
A user says, “The internet is down.”
You test:
- ping 8.8.8.8 works
- ping google.com fails
```
Answer:
```
What is more likely: full network outage or DNS issue?
- DNS issue
What evidence supports that?
- The IP works fine, but its the name and that is exactly what DNS is, its the adress getting the name of the website.
What would you check next?
- I would check if the url I typed in is correct or if google itself is down.
```
## What I observed
- The IP address my linux had
- The default route/gateway
- The bytes that were sent and received from google.com and ip address 8.8.8.8
## Evidence

| Evidence                            | Why it matters                                                                                                                                                                                                                                                                             |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 172.23.10.251                       | IP address of the linux system I’m using                                                                                                                                                                                                                                                   |
| 10.255.255.254                      | The IP address of google.com from using nslookup<br>GPT Help: nslookup returned 10.255.255.254 for google.com. This surprised me because 10.x.x.x is a private IP range, so I would want to verify whether this is caused by the lab environment, DNS configuration, VPN, WSL, or a proxy. |
| <BRODCAST ,MULTICAST ,UP ,LOWER_UP> | The status of the ethernet cable. This matters because it shows if its working with the words showing “UP” which means its active                                                                                                                                                          |

## What looked normal
- The Ip address and domain pinging with no packets lost
## What looked suspicious
-  The state being unknown for the loopback
- GPT Help: Nothing looked suspicious. The loopback state showing UNKNOWN does not appear suspicious because loopback interfaces often show that state.
## My verdict
- Everything is up and running correctly
- GPT Help: Network connectivity appears healthy. The system has an IPv4 address, a default gateway, and successful ping results to both 8.8.8.8 and google.com with 0% packet loss. DNS also appears to be working because google.com resolved and responded. I did not identify suspicious activity in this small network check.
## Confidence level

Low / Medium / <mark style="background: #BBFABBA6;">High</mark>

## What I would do next
- I would run the IP address through VirusTotal or AbuseIPDB
- GPT Help: I would check /etc/resolv.conf to see what DNS server Linux is using. I would also test another domain, such as example.com, and compare nslookup results. If DNS looked wrong, I would check whether the VM, WSL, VPN, or lab environment is affecting DNS.
## Questions I still have
- GPT Help:  
	- Why did nslookup return a private 10.x.x.x address for google.com?
	- What is the difference between eth0 and loopback?
	- Why does loopback sometimes show state UNKNOWN?
	- How do I check what DNS server Linux is using?
