# Lab Lab 014 - File Hashing and Integrity

## Goal
Practice using SHA-256 hashes to verify file integrity and observe how file changes affect hash values.
## Tool used
- Ubuntu/Linux terminal
- sha256sum

## What I checked
- I checked 2 files contents and their hash that outputted

## Commands I used
```
- mkdir day_29_lab
- cd day_29_lab/
- echo "This is my test evidence file." > evidence.txt
- cat evidence.txt
- sha256sum evidence.txt
- echo "A small change was made." >> evidence.txt
- echo "This is my test evidence file" > evidence2.txt
- sha256sum evidence2.txt
````

## Independent Analysis Task
1. What was the first hash?
	- **dcf26fc5d42f2e08e96667f1b75648e59844e931cdf2473df21e9cd58c34cbd0  evidence.txt**

2. What was the second hash?
	- **1e6d8baf8b8a4d77829fdbef6bb91a9c6b0c2e3448c951f950be32ed9c3fa554  evidence.txt**

3. What changed in the file?
	- The file did update and added “A small change was made.” to the end of the txt file.
4. Did the hash change?
	- Yes the hash changed. Starting with the first character being different than the first character on the first hash.
5. Was the file name the same?
	- Yes
6. If the file name stayed the same, why did the hash still change?
	- The hash still changed because of the hash algorithm. It reads every single byte of a file, and even a one-bit change on the data makes a different code produce. This keeps the integrity of files.
7. What does this prove about file integrity?
	- This proves that important security controls that make proven data integrity possible.
	- GPT Help: This proves that hashes can help verify file integrity. If a file’s hash changes, it means the file’s contents changed. If the hash stays the same, it provides evidence that the file has not been altered since the original hash was recorded.
8. How could this help in digital forensics or incident response?
	- This could help in digital forensics because its easier for them to see if a file has been altered or if a file has malware on it if its different from the original file.
	- GPT Help: In digital forensics or incident response, analysts can hash evidence files before and after handling them to prove whether the files were changed. Hashes can also help compare a suspicious file against known malware hashes or verify that a downloaded file matches the original.
9. What are you still unsure about with hashing?
	- File Integrity and how it helps in digital forensics

## Analyst challenge
1. Did a tiny punctuation/text difference create a different hash?
	- Yes, any sing bit change will create a different hash.
2. Why would that matter when verifying evidence?
	- That matters because everything could look good on paper, but you have to verify it deeply through the hash
## What I observed
- The file name stay the same
- The file contents change with the second echo just appending to the first file
- The hash change
## Evidence

| Evidence                                                                                                   | Why it matters                                                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| First SHA-256 hash: **dcf26fc5d42f2e08e96667f1b75648e59844e931cdf2473df21e9cd58c34cbd0  evidence.txt**<br> | - First Hash<br>- File name still the same<br>- contents in file changed<br>- GPT Help: Baseline hash before the file was changed                                     |
| Second SHA-256 hash:<br>**1e6d8baf8b8a4d77829fdbef6bb91a9c6b0c2e3448c951f950be32ed9c3fa554  evidence.txt** | - Second hash<br>- File name still the same<br>- Produced hash different<br>- Content inside file was just updated<br>- GPT Help: New hash after content was appended |

## My verdict
Did the file stay the same or change?
- The file stayed the same. The hash just changed
- GPT Help: The filename stayed the same, but the file contents changed. Because the contents changed, the SHA-256 hash changed. This shows the file was modified.

## Confidence level
<mark style="background: #BBFABBA6;">Low</mark> / Medium / High

## Questions I still have
- How are hashes used in real forensic chain-of-custody documentation?
- How do analysts use hashes to compare files against known malware databases?
