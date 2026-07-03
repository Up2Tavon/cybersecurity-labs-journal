# Lab 006 - Linux Command Line Basics

## Goal

Practice basic Linux commands that are useful for cybersecurity investigations and log analysis.

## Tool Used

- Linux terminal

## Commands Practiced

| Command | What it does |
|---|---|
| `pwd` | Shows the current directory |
| `ls` | Lists files and folders |
| `ls -la` | Lists files, folders, permissions, and hidden files |
| `mkdir` | Creates a new directory |
| `cd` | Changes directories |
| `touch` | Creates an empty file |
| `echo` | Prints text or writes text to a file |
| `cat` | Displays file contents |
| `grep` | Searches for matching text inside a file |

## Lab Steps

### 1. Checked my current directory
- pwd
What I saw:
- /home/up2tavon
- My home directory, the directory that I’m currently working in
### 2. Listed files
- ls
- ls -la
What I saw:
- The files in that folder
- cyber_lab
- with “ls -la” I saw all the hidden folder that are either less important or just more secretive I guess alongside the cyber_lab folder
### 3. Created a lab folder and notes file
- mkdir cyber_lab  
- cd cyber_lab  
- touch notes.txt  
- echo "This is my first Linux cybersecurity lab." > notes.txt  
- cat notes.txt
What I saw:
- The lab folder I created and was working inside that folder to create a file with the touch command
- When using cat after echo it showed the contents of what was inside the notes.txt which was the message I wrote
### 4. Created a fake authentication log
- echo "2026-06-30 login success user=Tavon ip=192.168.1.10" > auth.log  
- echo "2026-06-30 login failed user=admin ip=45.33.22.10" >> auth.log  
- echo "2026-06-30 login failed user=root ip=45.33.22.10" >> auth.log  
- echo "2026-06-30 login success user=Tavon ip=192.168.1.10" >> auth.log
What I saw:
- I didn’t cat into it after, so I just saw it be made real time, and after every echo it just did it and didn’t print nothing out in command line, but it was there inside the file
### 5. Searched the fake log with grep
- grep "failed" auth.log  
- grep "45.33.22.10" auth.log
What I saw:
- I seen only the files that were flagged with that keyword so it was easier to go through and see the suspicious activity
## Why This Matters for Cybersecurity

Linux commands are useful for investigating logs, searching for suspicious activity, and documenting evidence. Commands like `cat` and `grep` help analysts quickly find important events inside large files.
## What I Learned
- I learned how to create files and see the contents of them
- How to echo into a file and that will be the contents inside of it
## Questions I Still Have
- Why do we start the echo with “>”, then the rest are “>>”?
