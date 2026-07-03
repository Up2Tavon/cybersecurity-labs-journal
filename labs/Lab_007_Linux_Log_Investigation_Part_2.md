# Lab 007 - Linux Log Investigation Part 2

## Goal
Practice using Linux commands to investigate a fake authentication log and identify suspicious login activity.

## Tool Used

- Linux terminal

## Commands Practiced

| Command   | What it does                        |
| --------- | ----------------------------------- |
| `head`    | Shows the beginning of a file       |
| `tail`    | Shows the end of a file             |
| `less`    | Opens a file in a scrollable viewer |
| `grep`    | Searches for matching text          |
| `wc -l`   | Counts lines                        |
| `cut`     | Extracts parts of text              |
| `sort`    | Sorts output                        |
| `uniq -c` | Counts repeated values              |


## Fake Log File

I created a fake authentication log called:
- auth_day9.log
## Commands Used

### View the file

```
cat auth_day9.loghead auth_day9.logtail auth_day9.logless auth_day9.log
```

### Find failed logins

```
grep "failed" auth_day9.log
```

### Count failed logins

```
grep "failed" auth_day9.log | wc -l
```

Number of failed logins:
- 8

### Find root login attempts

```
grep "root" auth_day9.log
```

What I found:
- 3 failed login attempts
- 2 different ip’s being used to login
- first two logins were back to back with same ip, then the last time when they used a different ip it was later in the day like 40 mins later.

### Count failed login IPs

```
grep "failed" auth_day9.log | cut -d'=' -f3 | sort | uniq -c
```

What I found:
- the suspicious IPs were grouped and numbered
- 1 failed attempt from 203 ip, 4 failed attempts from 45, and 3 failed attempts from 91

## Suspicious Activity Found

The most suspicious IPs were:

|IP Address|Reason|
|---|---|
|45.33.22.10|Multiple failed logins against admin/root|
|91.199.212.40|Tried multiple usernames|
|203.0.113.77|Tried root login|

## My Beginner Verdict

This log shows possible brute-force or password guessing activity because multiple failed logins were attempted against high-value usernames like `admin` and `root`.

## Why This Matters for Cybersecurity

Security analysts use Linux commands to search through logs, identify suspicious activity, count events, and document evidence. Even simple commands like `grep`, `sort`, and `uniq -c` can help find patterns quickly.

## What I Learned
- I learned how to group and count the IPs with commands
- Not only can you just search and look at the data, but you can also group and manipulate the information being shown to make it readable or search faster for suspicious activity
## Questions I Still Have
- 
