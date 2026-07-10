# Lab 010 - SQL Filtering Basics

## Goal
Practice SQL filtering. This matters because security analysts often need to search through tables of users, login events, assets, alerts, or vulnerabilities. SQL helps you filter large data fast instead of reading every row manually.

## What I checked
- I checked the failed attempts from the users root, admin, test, and guest
- Filtered it to only see those attempts and also check suspicious IP addresses and filtered it to only see those IP address attempts
- Sorted the table to see the time of events it happened in order
## SQL queries I used

- SELECT * FROM login_events;
- SELECT * FROM login_events
	WHERE status = 'failed';
- SELECT * FROM login_events
	WHERE status = 'failed'
	AND username = 'root';
- SELECT * FROM login_events
	WHERE username = 'admin'
	OR username = 'root';
- SELECT * FROM login_events
	WHERE ip_address = '45.33.22.10';
- SELECT * FROM login_events
	ORDER BY event_time;
## Independent Analysis Task

1. What did you observe?
	- I observed different queries being used in code like text to sift and sort out the big table
	- A lot of failed attempts to sign into the system from different users like admin, guest, test and root
	- These failed attempts are from different IP addresses and some are from the same IP address
	- I was able to use a query to sort it by the username and that status
	- The most suspicious IP address was 45.33.22.10 because it was used by both admin and root on failed attempts
2. Which login events looked normal?
	- Users tavon and student
3. Which login events looked suspicious?
	- Users guest, root, admin, and test
4. What evidence supports your answer?
	- The admin and root being tried multiple times on different IP addresses
5. Which username(s) were targeted?
	- admin, and root
6. Which IP address looks most suspicious?
	- 91.199.212.40
	- 45.33.22.10
7. Does “Unknown” location/device matter? Why or why not?
	- Yes that matters because that means the threat actor is actively trying to hide what device they are using and their location. With that information you can rule out what kind of attack it was, either a bot attack or brute force or someone just forgetting their password. Also it proves the integrity and matches who was using what and what typical device they use.
	- GPT Help: The Unknown location/device is suspicious because the successful logins include normal location and device information, while the failed logins do not. However, I cannot prove the actor is hiding this information from this log alone.
8. What would you check next if this were a real alert?
	- Idk
	- GPT Help:
			- Check whether any login was successful after the failed attempts.
			- Check logs before and after the failed attempts.
			- Check if the same IPs appear in other systems or alerts.
			- Check whether admin or root login is normally allowed.
			- Check if MFA was enabled.
			- Check IP reputation in VirusTotal or AbuseIPDB.
			- Check whether the IPs are internal, external, VPN, cloud provider, or known company infrastructure.
9. What are you unsure about?
	- I was unsure about the test and guest, I’m thinking the threat actor tried to make it look normal or just tried to get in using something else to gain more access to possibly get the admin/root account

## What I observed
- I observed different queries being used in code like text to sift and sort out the big table
- A lot of failed attempts to sign into the system from different users like admin, guest, test and root
- These failed attempts are from different IP addresses and some are from the same IP address
- I was able to use a query to sort it by the username and that status
- The most suspicious IP address was 45.33.22.10 because it was used by both admin and root on failed attempts
	- GPT Help: 
		Most suspicious IP: 45.33.22.10
		Reason: It attempted both admin and root multiple times.
		Also suspicious: 91.199.212.40
		Reason: It attempted multiple usernames: guest, test, and admin.
## Evidence

| Evidence                                  | Why it matters                                                                                                                                                                                                 |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IP addresses: 45.33.22.10 & 91.199.212.40 | These two IP addresses were being used the most to try to get into the root and admin account                                                                                                                  |
| Users: tavon and student                  | These users had successful attempts to login in and each time they logged in it stayed consistent with their device and location proving that it was actually them. Thus supporting the integrity check on it. |

## What looked normal
- The successful attempts from username tavon with the location and device showing
- The IP staying consistent with user tavon on every successful attempt from that user 
- user student being successful with a different IP address from tavon and the device and location showing
## What looked suspicious
- The failed attempts
- The different IP addresses being used at different times
- The location and device being hidden on the failed attempts from the users
- The usernames trying to be accessed, root and admin are high level so whoever is trying to access those is very suspicious
## My verdict
- There is a threat actor actively trying to gain access into the highest levels of authority using different IP addresses and trying at different times.
	– Maybe they are trying to brute force their way in
- GPT Help: The logs show suspicious login activity that could indicate brute-force or password guessing attempts. The strongest evidence is multiple failed logins against privileged/default usernames like admin and root, especially from 45.33.22.10. Another suspicious IP is 91.199.212.40 because it tried multiple usernames such as guest, test, and admin.
## Confidence level
Low / <mark style="background: #BBFABBA6;">Medium</mark> / High
- GPT Help: My confidence is Medium because the activity is suspicious, but I would need more evidence before confirming an attack. I would check for successful logins after the failures, review more logs, check IP reputation, and confirm whether these IPs are expected or unknown.
## What I would do next
- I would block all those IP addresses and change the passwords to the accounts
- GPT Help: I would first escalate or investigate further. If the IPs are confirmed suspicious, I would recommend blocking them, reviewing the targeted accounts, checking for successful logins, and forcing password resets if there is evidence of compromise.
## Questions I still have
- 
