# Project 3 - Phishing Email Investigation Report

## Project Goal

The goal of this project was to investigate a suspicious email, identify phishing indicators, collect IOCs, check reputation information, and write a beginner-level security verdict.

## Scenario

A user received an email claiming to be from Coursera. The email warned that the user’s account would be suspended unless they verified their login immediately.

## Email Analyzed

```
Subject: Urgent: Verify Your Coursera Account

From: Coursera Support <support@coursera-security-login.com>

To: student@example.com

Hello,

We detected unusual activity on your Coursera account. Your account will be suspended within 24 hours unless you verify your login immediately.

Please verify your account here:
https://coursera-security-login.com/verify?session=934850

Failure to complete verification may result in permanent account closure.

Thank you,
Coursera Security Team
```

## Safety Note

I did not click the suspicious link or enter any credentials. I inspected the email text and documented indicators safely.

## Initial Observations

|Item|Observation|
|---|---|
|Claimed sender|Coursera Support|
|Sender email|support@coursera-security-login.com|
|Subject|Urgent: Verify Your Coursera Account|
|Main message|Account will be suspended unless user verifies login|
|Suspicious URL|https://coursera-security-login.com/verify?session=934850|
|Possible goal|Credential theft|

## Phishing Indicators

|Indicator|Why it is suspicious|
|---|---|
|Urgency|The email says the account will be suspended within 24 hours|
|Fear/threat language|It pressures the user with account closure|
|Suspicious sender domain|The sender uses coursera-security-login.com instead of a clear official Coursera domain|
|Login verification link|The link could lead to a fake login page|
|Generic security message|The message follows a common phishing pattern|

## IOCs Found

|IOC Type|Value|
|---|---|
|Sender email|support@coursera-security-login.com|
|Domain|coursera-security-login.com|
|URL|https://coursera-security-login.com/verify?session=934850|
|Subject line|Urgent: Verify Your Coursera Account|
|Claimed brand|Coursera|

## Reputation Check

### Tool Used

- VirusTotal

### Indicator Checked

```
coursera-security-login.com
```

### Result

```
Result: 
- Detection ratio: 0/92
- Community score: No community score
Notes:
- Most of the checkers say its clean
- Like example.com 28 checkers have not been rated and have a status of unrated
- A clean or empty VirusTotal result foes not prove a domain is safe. The domain still looks suspicious because it imitates Coursera and uses urgency.
```

### Important Note

A clean or empty reputation result does not automatically prove that something is safe. The email can still be suspicious based on the sender domain, urgency, and request to verify login credentials.

## Beginner Analysis

This email appears to be a phishing attempt. It impersonates Coursera, creates urgency, threatens account suspension, and includes a login verification link using a suspicious domain.

The likely goal is to trick the user into clicking the link and entering their account credentials on a fake login page.

## Beginner Verdict

```
Likely phishing
```

## Recommended Action

If this were a real email, I would recommend:

- Do not click the link
- Do not reply to the sender
- Do not enter login credentials
- Report the email to the security team or email provider
- Block or investigate the suspicious sender/domain
- Search for similar emails sent to other users
- Document the IOCs for future detection

## Skills Practiced

- Phishing email analysis
- IOC identification
- Suspicious domain review
- Reputation-check documentation
- Writing a beginner security verdict
- Creating recommended response actions

## What I Learned

- Phishing emails often use urgency and fear.
- Sender domains should be checked carefully.
- IOCs help analysts document and track suspicious activity.
- Reputation tools are useful, but they are not perfect.
- A security analyst should avoid clicking suspicious links directly.

## Questions I Still Have
- 
## Conclusion

This project helped me practice investigating a suspicious email safely. I identified phishing indicators, collected IOCs, documented reputation-check information, and wrote a beginner-level verdict and recommended response.
