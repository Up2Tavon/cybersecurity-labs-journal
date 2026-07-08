# Lab 009 - Reputation Checks with VirusTotal and AbuseIPDB

## Goal

Practice checking domains, URLs, and IP addresses using reputation tools without directly visiting suspicious links.

## Tools Used

- VirusTotal
- AbuseIPDB

## Safety Rule

I should not directly visit suspicious links during an investigation. Instead, I can copy the domain, URL, IP address, or hash into a reputation tool and document the results.

## What VirusTotal Is

VirusTotal is a reputation-checking tool that can analyze domains, URLs, IP addresses, and file hashes. It helps analysts see whether security vendors have flagged an indicator as malicious or suspicious.

## What AbuseIPDB Is

AbuseIPDB is a reputation-checking tool focused on IP addresses. It can show whether an IP address has been reported for abusive behavior.

## Indicators Checked

| Indicator                   | Type       | Tool Used              | Result / Notes                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Beginner Verdict                                              |
| --------------------------- | ---------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| example.com                 | Domain     | VirusTotal             | - Looks pretty safe<br>- Everything shows clean from all the checkers on there<br>- 28 checkers have not been rated for this site ro it just says unrated                                                                                                                                                                                                                                                                                                             | - This site is safe and clean                                 |
| coursera-security-login.com | Domain     | VirusTotal             | - Most of the checkers say its clean<br>- Like example.com 28 checkers have not been rated and have a status of unrated                                                                                                                                                                                                                                                                                                                                               | - This site is safe and clean                                 |
| 8.8.8.8                     | IP address | VirusTotal / AbuseIPDB | **VirusTotal:**<br>	- IP address<br>	- Crowdsourced context flagged it as medium 2 years ago:<br>	  - ThreatFox IOCs for 2023-09-10<br>		- AsyncRAT botnet C2 server (confidence level: 100%)<br>**AbuseIPDB:<br>  - There are a lot of people from different countries getting reported for trying to hack into this IP<br>  - The IP address has been reported a total of 152 times from 83 distinct sources<br>  - The first report on this IP was March 19th 2026 | - This site is safe and clean<br>- This IP is safe and secure |
| 1.1.1.1                     | IP address | AbuseIPDB              | - This IP was reported 1,173 times<br>- Based in Australia<br>- First report was July 19th 202                                                                                                                                                                                                                                                                                                                                                                        | - This IP is safe and secure                                  |

## VirusTotal Observations

### example.com

```
Detection ratio: 0/92
Community score: -4
Notes:
- Looks pretty safe
- Everything shows clean from all the checkers on there
- 28 checkers have not been rated for this site so it just says unrated
Verdict: 
- This site is safe and clean
```

### coursera-security-login.com

```
Detection ratio: 0/92
Community score: No community score
Notes: 
- Most of the checkers say its clean
- Like example.com 28 checkers have not been rated and have a status of unrated
Verdict:
- This site is safe and clean
```

### 8.8.8.8

```
Detection ratio: 0/92
Community score: +57
Notes:
- VirusTotal:
	- IP address
	- Crowdsourced context flagged it as medium 2 years ago:
	  - ThreatFox IOCs for 2023-09-10
		- AsyncRAT botnet C2 server (confidence level: 100%)
Verdict:
- This site is safe and clean
```

## AbuseIPDB Observations

### 8.8.8.8

```
Abuse confidence score: 0%
Owner / ISP: Google LLC
Notes:
- AbuseIPDB:
  - There are a lot of people from different countries getting reported for trying to hack into this IP
  - The IP address has been reported a total of 152 times from 83 distinct sources
  - The first report on this IP was March 19th 2026
Verdict:
- This IP is safe and secure
```

### 1.1.1.1

```
Abuse confidence score: 0%
Owner / ISP: APNIC and Cloudflare DNS Resolver project
Notes:
- This IP was reported 1,173 times
- Based in Australia
- First report was July 19th 202
Verdict:
- This IP is safe and secure
```

## What I Learned

- Reputation tools help analysts investigate suspicious indicators safely.
- I should check domains and IPs without directly visiting suspicious links.
- A clean reputation result does not always prove something is safe.
- IOCs can include domains, URLs, IP addresses, hashes, sender emails, and attachment names.

## Why This Matters for Cybersecurity

In phishing and incident response investigations, analysts collect IOCs and check their reputation before recommending actions like blocking a domain, reporting an email, or escalating an alert.

## Questions I Still Have
- Why are not all the checkers rated on VirusTotal?
- What does this mean?: 
	- Crowdsourced context flagged it as medium 2 years ago:
	  - ThreatFox IOCs for 2023-09-10
		- AsyncRAT botnet C2 server (confidence level: 100%)
- Why are these IPs now just recently being attacked is it because the advance in technology?
- Why are hackers trying to gain that IP?
- Who even reports these guys trying to get these IPs
