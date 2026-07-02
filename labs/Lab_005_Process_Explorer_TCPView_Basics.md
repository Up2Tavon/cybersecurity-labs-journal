# Lab 005 - Process Explorer and TCPView Basics

## Goal

Learn how to observe running processes and active network connections using Sysinternals tools.

## Tools Used

- Process Explorer
- TCPView
- Web browser

## What Process Explorer Does

Process Explorer shows running processes on a Windows system. It can help an analyst understand what programs are running, who made them, how much CPU/memory they use, and what parent process launched them.

## What TCPView Does

TCPView shows active network connections on a Windows system. It can help an analyst see which processes are communicating over the network and what remote addresses/ports they are connecting to.

## Process Explorer Observations

| Process Name |   PID | Company/Description                    | Why it looked normal                                         |
| ------------ | ----: | -------------------------------------- | ------------------------------------------------------------ |
| Chrome.exe   | 13136 | Google LLC/Google Chrome               | It is signed by a known company and matches an app I opened. |
| Explorer.exe |  8532 | Microsoft Corporation/Windows Explorer | It is signed by a known company and matches an app I opened. |
| Steam.exe    |  5036 | Valve Corporation/Steam                | It is signed by a known company and matches an app I opened. |

## Process Investigated More Closely
### Process Name
Chrome.exe
	### PID
		13136
	### Company / Description
		Google LLC/Google Chrome
	### Parent Process
		Chrome.exe
	### My Verdict
		This process appeared:
			<mark style="background: #FFB86CA6;">Normal</mark> / Suspicious / Unsure
			Reason:
				- Known LLC and just opened it up so it matched with the task I was doing at hand.
## TCPView Observations

| Process Name       | Remote Address | Remote Port | State       | What I think it was                                                                                                                                                                                          |
| ------------------ | -------------- | ----------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| chrome.exe         | 32.195.150.54  | 443         | Established | I think this is google chrome, specifically one of the tabs I have opened. there are a lot of chomre.exe Processes, so they might be the tabs I have open for Chrome.                                        |
| Stardew Valley.exe | 91.222.185.227 | 443         | Established | I'm surprised it had a remote port of 443. That means Steam might be running the games from a web browser of some sorts. That make me wonder is that how all games are ran through some form of web browser? |
| steam.exe          | 162.254.195.69 | 27018       | Established | I just opened steam to test what pops up, so it matches what I just opened. I’m confused on that port number though.                                                                                         |

## Port 443 Observation

I observed connections using remote port 443. Port 443 is commonly used for HTTPS, which means encrypted web traffic.

## What I Learned

Process Explorer helps me understand what is running on my computer. TCPView helps me understand what those processes are connecting to. Together, these tools are useful for basic investigation because they connect system activity with network activity.

## Questions I Still Have

- What is Steam’s port number and what does it mean?
- Why does Stardew Valley have a port number of 443?
- Are all games ran through a web browser? or use port 443?
