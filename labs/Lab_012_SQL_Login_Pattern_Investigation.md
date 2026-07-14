# Lab 012 - SQL Login Pattern Investigation

## Goal
Practicing **finding patterns in login data**, not just running basic SQL.
## What I checked
- I checked for failed logins
- Counted the failed logins by IP addresses
- Counted the failed logins by usernames
- Showed the failed logins from the admin/root accounts
- Showed the failed logins from the admin/root/guest/test accounts
## SQL queries I used

- SELECT * FROM login_events;
- SELECT * FROM login_events
	WHERE status = 'failed';
- SELECT ip_address, COUNT(\*) AS failed_count
	FROM login_events
	WHERE status = 'failed'
	GROUP BY ip_address
	ORDER BY failed_count DESC;
- SELECT username, COUNT(\*) AS failed_count
	FROM login_events
	WHERE status = 'failed'
	GROUP BY username
	ORDER BY failed_count DESC;
- SELECT * FROM login_events
	WHERE status = 'failed'
	AND username IN (‘root’, ‘admin’);
- SELECT * FROM login_events
	WHERE status = 'failed'
	AND username IN (‘root’, ‘admin’, ‘guest’, ‘test’);
- SELECT * FROM login_events
	WHERE ip_address = '91.199.212.40';

## Independent Analysis Task
1. Which IP address had the most failed logins?
	- Two IP addresses had the same amount of failed logins. Those IP addresses being: 91.199.212.40 & 45.33.22.10 with three failed attempts each.
2. Which username had the most failed login attempts?
	- Admin had the most failed login attempts.
3. Did the suspicious IP target one account or multiple accounts?
	- The suspicious IP targeted multiple accounts with those accounts being admin and root.
4. Does this look more like brute force, password spraying, or normal failed logins?
	- This looks like brute force.
5. What evidence supports your answer?
	- This looks like brute force because of the time of events and the trying admin multiple times with not just one IP, but two IP addresses. That could mean that the first IP address got blocked from the brute force, so the threat actor changed their IP to keep trying.
6. What looks normal in the dataset?
	- The user tavon having two successful attempts at different times. Also with the device and location staying consistent with those attempts.
7. What are you unsure about?
	- I’m unsure about the failed attempts from test and guest.
8. What would you check next if this were a real SOC alert?
	- I would check whether 45.33.22.10 appears in other logs, whether any successful login happened after the failed attempts, whether the IP has a bad reputation in VirusTotal or AbuseIPDB, and whether admin/root login is even allowed in this environment.
	- GPT Help: I would also check whether MFA was triggered, whether the accounts were locked, and whether any endpoint activity happened after the login attempts.

## Analyst Challenge
1. Show all failed logins where the username is admin, root, guest, or test.
	- SELECT * FROM login_events
		WHERE status = 'failed'
		AND username IN (‘root’, ‘admin’, ‘guest’, ‘test’);
2. Show all events from the IP address with the highest failed_count.
	- SELECT * FROM login_events
		WHERE ip_address = '91.199.212.40';
Which piece of evidence is strongest: the IP address pattern, the username pattern, or the Unknown device/location? Why?
	- The strongest evidence is the IP address pattern, because it that’s basically the devices name whether its a proxy or VPN, it still is always logged no matter what so its the most reliable piece of information to track.
	- GPT Help: The strongest evidence is the IP address pattern because repeated failed logins from the same IPs show a pattern of activity. However, an IP address does not always identify one exact device because it could be a VPN, proxy, shared network, or cloud server.

## What I observed
- I observed usernames grouped by their failed count'
- IP address grouped by their failed count to visualize it better and see which one is the highest
- The failed and successful attempts from the users and the time of their events they tried to log on to the system
## Evidence

| Evidence                               | Why it matters                                                                                                                                                                             |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 45.33.22.10                            | It was the highest failed IP address that was being used to try to get into multiple different accounts.                                                                                   |
| 91.199.212.40                          | It was the highest failed IP address that was being used to try to get into multiple different accounts.                                                                                   |
| usernames: admin, root, guest and test | All these usernames had only failed attempts from what my log table showed. This is very suspicious but could be that someone forgot they password or that these account don’t even exist. |

## What looked normal
- The successful events from the usernames tavon, and student
- The location and device being consistent with the successful events
## What looked suspicious
-  The failed attempts trying to access the usernames root and admin
- The guest and test failed attempts
## My verdict
- Someone is trying to brute force to get into admin, and the system automatically blocked the IP, so they used another IP to keep trying to get in.
- GPT Help: This activity looks like possible brute-force or password guessing activity. Two IP addresses, 45.33.22.10 and 91.199.212.40, had the highest number of failed login attempts. The targeted usernames included admin, root, guest, and test, which are commonly targeted or default-style usernames. I cannot confirm that the attacker was blocked or changed IP addresses without additional firewall, authentication, or SIEM logs. My confidence is medium because the activity is suspicious, but I do not yet have evidence of a successful compromise.
## Confidence level

Low / <mark style="background: #BBFABBA6;">Medium</mark> / High
- GPT Help: The repeated failed logins against admin/root are suspicious, but I do not have enough evidence to confirm compromise. I would need more logs, reputation checks, and successful-login data.

## What I would do next
- I would check the IP address in VirusTotal or AbuseIPDB
## Questions I still have
- 
