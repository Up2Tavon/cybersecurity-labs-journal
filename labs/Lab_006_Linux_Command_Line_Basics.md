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
- 
### 2. Listed files
- ls
- ls -la
What I saw:
- d
### 3. Created a lab folder and notes file
- mkdir cyber_lab  
- cd cyber_lab  
- touch notes.txt  
- echo "This is my first Linux cybersecurity lab." > notes.txt  
- cat notes.txt
What I saw:
- d
### 4. Created a fake authentication log
- echo "2026-06-30 login success user=Tavon ip=192.168.1.10" > auth.log  
- echo "2026-06-30 login failed user=admin ip=45.33.22.10" >> auth.log  
- echo "2026-06-30 login failed user=root ip=45.33.22.10" >> auth.log  
- echo "2026-06-30 login success user=Tavon ip=192.168.1.10" >> auth.log
What I saw:
- d
### 5. Searched the fake log with grep
- grep "failed" auth.log  
- grep "45.33.22.10" auth.log
What I saw:
- d
## Why This Matters for Cybersecurity

Linux commands are useful for investigating logs, searching for suspicious activity, and documenting evidence. Commands like `cat` and `grep` help analysts quickly find important events inside large files.
## What I Learned
- 
## Questions I Still Have
- 
