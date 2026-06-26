# Lab 003 - Top 25 Ports Cheat Sheet

## Goal
Learn common ports that appear in networking and cybersecurity investigations.

## Most Important Beginner Ports

| Port  | Protocol | What it is used for         | Security note                     |
| ----- | -------- | --------------------------- | --------------------------------- |
| 20/21 | FTP      | File transfer               | Usually insecure if not encrypted |
| 22    | SSH      | Secure remote login         | Common admin access port          |
| 23    | Telnet   | Remote login                | Insecure, old, avoid              |
| 25    | SMTP     | Sending email               | Used by mail servers              |
| 53    | DNS      | Turns domain names into IPs | Very common in traffic            |
| 67/68 | DHCP     | Gives devices IP addresses  | Used when joining networks        |
| 80    | HTTP     | Unencrypted web traffic     | Not secure by itself              |
| 110   | POP3     | Email retrieval             | Older email protocol              |
| 143   | IMAP     | Email retrieval             | Used to read email                |
| 443   | HTTPS    | Encrypted web traffic       | Most websites use this            |
| 445   | SMB      | Windows file sharing        | Important in Windows networks     |
| 3389  | RDP      | Remote Desktop              | Common attack target if exposed   |
## Extra Common Ports

| Port | Protocol | What it is used for |
|---|---|---|
| 123 | NTP | Time synchronization |
| 135 | RPC | Windows remote procedure calls |
| 137-139 | NetBIOS | Older Windows networking |
| 161/162 | SNMP | Network device monitoring |
| 389 | LDAP | Directory services |
| 465 | SMTPS | Secure email sending |
| 587 | SMTP Submission | Sending email securely |
| 993 | IMAPS | Secure IMAP email |
| 995 | POP3S | Secure POP3 email |
| 1433 | MSSQL | Microsoft SQL Server |
| 3306 | MySQL | MySQL database |
| 5432 | PostgreSQL | PostgreSQL database |
| 5900 | VNC | Remote desktop/control |

## Wireshark Observations

### tcp.port == 443
What I saw: 
- A lot of ports source and destination of 443 
- Port 443 means HTTPS, so this is encrypted website traffic

### dns or udp.port == 53
What I saw:
- Port 53 turns domain names into IPs
	– Very common in traffic
	– My computer asking where a website lives

### tcp.port == 80
What I saw:
- 3 entries
	- 2 of the entries were 63754→80, and 1 entry was 80→63754
- Port 80 means HTTP, so this is unencrypted website traffic
	– Not secure by itself

### tcp.port == 25
What I saw:
- No entries/traffic
- Port 25 means SMTP; sending mail
	– Used by mail servers

### tcp.port == 22
What I saw:
- No entries
- I did not see SSH traffic because I was not remotely logging into another computer
- Port 22 means secure remote login
	– common admin access port
### tcp.port == 80
What I saw:
- 3 entries
	- 2 of the entries were 63754→80, and 1 entry was 80→63754
- Port 80 means HTTP, so this is unencrypted website traffic
	– Not secure by itself


## What I Learned
Ports help identify what service or protocol a computer is using. In Wireshark, I can filter by port to narrow down traffic.

## Questions I Still Have
-
