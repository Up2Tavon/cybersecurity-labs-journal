# Lab 008 - Phishing Email Investigation Basics

## Goal

Practice analyzing a suspicious email and identifying phishing indicators without opening attachments or visiting suspicious links.

## Tool Used

- Manual investigation
- Cybersecurity notes

## Safe Investigation Rule

I should not click suspicious links, download unknown attachments, or enter credentials into suspicious websites. The goal is to inspect and document indicators safely.

## Fake Email Analyzed

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

## Phishing Checklist
– Who sent it?
– Does the sender look fake?
– Is the message urgent or threatening?
– Are there suspicious links?
– Does the domain match the company?
– Are there attachments?
– What are the IOCs?
– What action should be taken?
- **IOC** means **Indicator of Compromise**. In a phishing email, IOCs can be:
	- Suspicious sender email
	- Suspicious domain
	- Suspicious URL
	- Suspicious IP address
	- File hash
	- Attachment name
	- Subject line

## Investigation Questions

### Sender

```
support@coursera-security-login.com
```

### Claimed Organization

```
Coursera
```

### Suspicious Domain

```
coursera-security-login.com
```

### Suspicious URL

```
https://coursera-security-login.com/verify?session=934850
```

## Phishing Indicators Found

|Indicator|Why it is suspicious|
|---|---|
|Urgent subject line|Creates pressure to act quickly|
|Account suspension threat|Tries to scare the user|
|Suspicious sender domain|Does not match the real Coursera domain|
|Suspicious login link|Could lead to credential theft|
|Generic security message|Common in phishing attempts|

## IOCs Found

| IOC Type     | Value                                                     |
| ------------ | --------------------------------------------------------- |
| Sender email | support@coursera-security-login.com                       |
| Domain       | coursera-security-login.com                               |
| URL          | https://coursera-security-login.com/verify?session=934850 |
| Subject      | Urgent: Verify Your Coursera Account                      |

## Beginner Verdict

This email appears suspicious and likely phishing.

## Reason for Verdict

The email uses urgency, threatens account suspension, and includes a login link using a suspicious domain that does not clearly match the real organization.

## Recommended Action

If this were a real email, I would recommend:

- Do not click the link
- Do not enter login credentials
- Report the email to the security team or email provider
- Block or review the suspicious sender/domain
- Search for similar emails in other mailboxes
- Document the IOCs

## What I Learned

- Phishing emails often use urgency and fear.
- Sender domains should be checked carefully.
- IOCs can include sender emails, domains, URLs, subjects, and attachment names.
- A security analyst should document findings clearly.

## Questions I Still Have
- 
