# Project 2 - Linux Log Investigation

## Project Goal

The goal of this project was to investigate a fake Linux authentication log and identify suspicious login activity using basic Linux command line tools.

## Scenario

I was given a fake authentication log containing successful logins, failed logins, password reset activity, usernames, and IP addresses. My task was to review the log, find suspicious entries, count failed login attempts, identify targeted accounts, and make a beginner-level security conclusion.

## Tool Used

- Linux terminal

## Log File Investigated
- auth_day9.log

## Investigation Questions
- How many failed logins happened?
	– There were 8 failed login attempts.
- Which IP had the most failed logins?
	– 45.33.22.10 had the most failed attempts.
- Which usernames were targeted?
	– Root
	– Admin
	– Guest
	– Test
- Was this normal or suspicious?
	– Suspicious because of the same usernames being used with different IP addresses
	– This activity looks suspicious and could represent brute-force login attempts or password guessing.
- What would a security analyst do next?
	– Review whether any login attempts were successful after the failures
	– Check if the suspicious IPs appear in other logs
	– Block or monitor suspicious IP addresses if confirmed malicious
	– Ensure privileged accounts use strong passwords and MFA
	– Document the findings for escalation

## Commands Used

### View the log file

```
cat auth_day9.log
```

Purpose:

```
Displayed the full contents of the log file.
```

### View the beginning and end of the log

```
head auth_day9.log
tail auth_day9.log
```

Purpose:

```
Allowed me to quickly check the first and last entries in the log.
```

### Search for failed logins

```
grep "failed" auth_day9.log
```

Purpose:

```
Filtered the log to only show failed login attempts.
```

### Count failed logins

```
grep "failed" auth_day9.log | wc -l
```

Result:

```
8
```

Purpose:

```
Counted how many failed login attempts appeared in the log.
```

### Search for root login attempts

```
grep "root" auth_day9.log
```

Result:

```
3 failed login attempts from the root user at different times, and using a different IP address

- 2026-07-03 08:04:02 login failed user=root ip=45.33.22.10
- 2026-07-03 08:05:21 login failed user=root ip=45.33.22.10
- 2026-07-03 08:45:09 login failed user=root ip=203.0.113.77
```

Purpose:

```
Searched for login attempts involving the root account, which is important because root is a high-privilege Linux account.
```

### Count failed login attempts by IP address

```
grep "failed" auth_day9.log | cut -d'=' -f3 | sort | uniq -c
```

Result:

```
Sorted and grouped the failed attempts from each user together. With the groupings it also numbered the amount that each attempt failed.

- 1 203.0.113.77
- 4 45.33.22.10
- 3 91.199.212.40
```

Purpose:

```
Extracted IP addresses from failed login events, sorted them, and counted repeated IPs.
```

## Suspicious Entries Found

|IP Address|Activity|Why it is suspicious|
|---|---|---|
|45.33.22.10|Multiple failed logins against admin and root|Repeated attempts against privileged/default usernames|
|91.199.212.40|Failed logins against guest, test, and admin|Tried multiple usernames, which may indicate password guessing|
|203.0.113.77|Failed root login|Root login attempts are high-risk and should be reviewed|

## Targeted Usernames

```
admin
root
guest
test
```

## Beginner Analysis

The log shows multiple failed login attempts against accounts such as `admin` and `root`. These usernames are commonly targeted because they may have elevated privileges or are common default accounts.

The IP address `45.33.22.10` appears especially suspicious because it made repeated failed login attempts against both `admin` and `root`.

## Beginner Verdict

This activity looks suspicious and could represent brute-force login attempts or password guessing.

## Recommended Response

If this were a real investigation, I would recommend:

- Review whether any login attempts were successful after the failures
- Check if the suspicious IPs appear in other logs
- Block or monitor suspicious IP addresses if confirmed malicious
- Ensure privileged accounts use strong passwords and MFA
- Document the findings for escalation

## Skills Practiced

- Reading Linux log files
- Searching logs with `grep`
- Counting events with `wc -l`
- Using pipes
- Extracting fields with `cut`
- Sorting and counting repeated values
- Identifying suspicious login behavior
- Writing a beginner security investigation report

## What I Learned

- Linux commands can quickly find suspicious activity in logs.
- Failed logins against `admin` and `root` should be investigated.
- Counting repeated IP addresses helps identify patterns.

## Questions I Still Have
- 
## Conclusion

This project helped me practice beginner log investigation using Linux commands. I learned how to search for suspicious login activity, count failed attempts, identify repeated IP addresses, and document my findings like a security analyst.
