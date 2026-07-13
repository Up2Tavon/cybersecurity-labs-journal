# Lab 011 - SQL Login Investigation

## Goal
Use SQL to find evidence, explain what happened, and decide what looks suspicious.

## What I checked
- Filtered to find all failed logins only
- Filtered to find all successful logins only
- Found activity from unknown locations
- Filtered to find failed logins from unknown devices
- Filtered to find activity targeting privileged/default usernames
## SQL queries I used

- SELECT * FROM login_events;
- SELECT * FROM login_events
	WHERE status = 'failed';
- SELECT * FROM login_events
	WHERE status = 'success';
- SELECT * FROM login_events
	WHERE location = 'Unknown';
- SELECT * FROM login_events
	WHERE status = 'failed'
	AND device = ‘Unknown’;
- SELECT * FROM login_events
	WHERE username = 'admin'
	OR username = ‘root’;
- SELECT COUNT(\*) FROM login_events;
- SELECT COUNT(\*) FROM login_events
	WHERE status = ‘failed’;

## Independent Analysis Task
1. How many total login events are there?
	- 10 
2. How many failed login events are there?
	- 7
3. Which events look normal?
	- The successful events from the usernames tavon, and student 
4. Which events look suspicious?
	- The failed attempts trying to access the usernames root and admin
5. What evidence makes them suspicious?
	- The evidence that makes them suspicious is the location and device being unknown. Also that admin and root were tried multiple times with the same IP address, then with a different IP address.
6. Which IP address would you investigate first?
	- I would investigate 45.33.22.10 first because that IP address was used the most to get into the root and admin account
7. Which username looks most targeted?
	- The username that looks the most targeted is admin because it was tried 3 different times with different IP addresses and at different times of day.
8. Does “Unknown” location/device automatically mean malicious?
	- No it doesn’t automatically mean suspicious because it could have been just a student using a VPN or the program not reading it correctly and making an error.
9. What else would you need before making a final decision?
	- I would need to do an in depth analysis on the IP addresses trying to get into root and admin account

## Analyst Challenge
1. Show failed logins from Unknown locations.
	- SELECT * FROM login_events
		WHERE status = 'failed'
		AND location = ‘Unknown’;
2. Show all activity from the IP you think is most suspicious.
	- SELECT * FROM login_events
		WHERE ip_address = '45.33.22.10';
3. Show only successful logins from California.
	- SELECT * FROM login_events
		WHERE status = 'success'
		AND location = ‘California’;
4. Show all failed logins for admin or root.
	- SELECT * FROM login_events
		WHERE status = 'failed'
		AND (username = ‘root’ OR username = ‘admin’);
	- SELECT * FROM login_events
		WHERE status = 'failed'
		AND username IN (‘root’, ‘admin’);
Which query gave you the strongest evidence? Why?
- The IP query gave me the strongest evidence because it showed me who was trying to access the highest privilege accounts and possible explains that this is an attack since it was trying to be accessed from the same IP address multiple times.

## What I observed
- I observed different IP addresses being used to get into accounts and whether it was a success or fail to get into the account
## Evidence

| Evidence                     | Why it matters                                                                                                                                                                                       |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 45.33.22.10                  | It was the most suspicious IP address that was being used to try to get into admin and root multiple different times.                                                                                |
| usernames: tavon and student | These were the only successful attempts and proves integrity with the account.<br>GPT Help: These logins looked more normal because they were successful logins from California using known devices. |
| usernames: guest and test    | These were different IP addresses than the root and admin attempts, so these are kind of suspicious, but it could have been someone our team doing penetration test.                                 |

## What looked normal
- The successful events from the usernames tavon, and student 
## What looked suspicious
-  The failed attempts trying to access the usernames root and admin
## My verdict
- This may be a targeted attack to get into the admin and root account due to the IP address being used multiple times with failed attempts to get into those accounts
## Confidence level

Low / <mark style="background: #BBFABBA6;">Medium</mark> / High

## What I would do next
- I would look more into the suspicious IP address
- GPT Help: I would check whether 45.33.22.10 appears in other logs, whether any successful login happened after the failed attempts, whether the IP has a bad reputation in VirusTotal or AbuseIPDB, and whether admin/root login is even allowed in this environment.
## Questions I still have
- 
