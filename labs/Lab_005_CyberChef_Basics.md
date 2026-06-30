# Lab 005 - CyberChef Basics

## Base64 Decode

Input:
SGVsbG8sIEN5YmVyc2VjdXJpdHkh

Operation:
From Base64

Output:
Hello, Cybersecurity!

What I learned:
Base64 is not encryption. It is encoding. It changes how text is represented, but it can easily be reversed.

## Base64 Encode

Input:
My first CyberChef lab

Operation:
To Base64

Output:
[TXkgZmlyc3QgQ3liZXJDaGVmIGxhYg==]

What I learned:
Encoding can convert readable text into another format, but it is reversible.

## SHA-256 Hash

Input:
password123

Operation:
SHA2 / SHA-256

Output:
[ef92b778bafe771e89245b89ecbc08a44a4e166c06659911881f383d4473e94f]

What I learned:
A hash is like a fingerprint for data. It is not meant to be reversed like Base64.

## Fake IOC Practice

Fake suspicious domain:
login-microsoft-security-check.example

Base64 output:
	[**aHR0cDovL2xvZ2luLW1pY3Jvc29mdC1zZWN1cml0eS1jaGVjay5leGFtcGxl**]

SHA-256 hash:
[**58009a3f8d37b97c0dbfd4af2767e891beb9286f84eba179821a66ade0f27905**]

Defanged version:
[**hxxp[://]login-microsoft-security-check[.]example**]

Why defanging matters:
Defanging makes suspicious links safer to document because someone cannot accidentally click them.

## Key Takeaways

- Base64 is encoding, not encryption.
- Encoding is usually reversible.
- Hashing creates a fingerprint of data.
- Defanging makes suspicious links safer to document.
- CyberChef is useful for investigations, IOCs, logs, and phishing analysis.

## Questions I Still Have

- 
