# OIBSIP
# Task 1: Basic Network Scanning with Nmap

**Name:** Shlok Pandey
**Track:** Security Analyst | Oasis Infobyte SIP
**Task:** Basic Network Scanning with Nmap

## What is Nmap?
Nmap (Network Mapper) is a free, open-source tool that finds which devices are online on a network, which ports are open, and which services run on them.

## Why network scanning matters
Attackers scan networks to find open ports and outdated services they can exploit. Defenders run the same scans first so they can close unneeded ports and fix weak services before an attacker finds them.

## Ethics and permission
I scanned only devices I own: my own phone and my own laptop (localhost). Scanning devices without permission is illegal, so this task was done only on my own devices.

## Lab setup
| Item | Details |
|---|---|
| Host computer | ASUS Vivobook, Windows 11 |
| Linux environment | Ubuntu on Windows Subsystem for Linux (WSL) |
| Tool | Nmap 7.98 |
| Target 1 | My own phone, IP 100.75.93.186 (private VPN address) |
| Target 2 | My own laptop, localhost (127.0.0.1) |
| Scan date | 2026-11-11 |

## Installation steps
1. **Turn on WSL:** On Windows I opened "Turn Windows features on or off", ticked **Windows Subsystem for Linux** (and Virtual Machine Platform), and clicked OK.
2. **Restart:** I rebooted the laptop so the feature became active.
3. **Install Ubuntu:** I installed **Ubuntu** from the Microsoft Store and opened it.
4. **Create a user:** On first launch I created a Linux username and password.
5. **Update packages:**
   `sudo apt update`
6. **Install Nmap:**
   `sudo apt install nmap -y`
7. **Check the installation:**
   `nmap --version`
   It showed Nmap 7.98 (platform x86_64-pc-linux-gnu).
8. **Install and start SSH (to have a service to scan on localhost):**
   `sudo apt install openssh-server -y`
   `sudo service ssh start`



![Nmap version](screenshots/00_nmap_version.png)



## Commands used
| Command | What it does |
|---|---|
| `nmap --version` | Shows the installed Nmap version |
| `nmap 100.75.93.186` | Basic scan of the 1000 most common ports |
| `sudo nmap -sV 100.75.93.186` | Service version scan: tries to identify the software on each open port |
| `sudo nmap -O 100.75.93.186` | OS detection: guesses the operating system |
| `sudo nmap -sV -O 100.75.93.186 -oN nmap_scan_results.txt` | Runs both scans and saves the output to a file |
| `nmap -sV localhost` | Service version scan of my own laptop |

## Scan results

### 1. Basic scan (my phone)
- Host is up.
- All 1000 scanned ports were closed. No open ports were shown.
- Scan finished in [fill from your screenshot] seconds.



![Basic scan](screenshots/01_basic_scan.png)



### 2. Service version scan, -sV (my phone)
- Host is up.
- All 1000 ports were closed, so there were no services to identify.
- Scan finished in [fill from your screenshot] seconds.



![Service version scan](screenshots/02_service_scan.png)



### 3. OS detection, -O (my phone)
- Device type: general purpose.
- Running: Linux 2.6.X, 3.X, 4.X or 5.X.
- OS details: Linux 2.6.32 - 3.10, Linux 3.2 - 4.14, Linux 4.15 - 5.19.
- Network distance: 2 hops.
- Nmap warned that this result may be unreliable because it found no open port to test against.
- Scan finished in [fill from your screenshot] seconds.



![OS detection](screenshots/03_os_detection.png)



### 4. Combined scan saved to file (my phone)
I ran `sudo nmap -sV -O 100.75.93.186 -oN nmap_scan_results.txt` on 2026-11-11 at 06:51 (UTC).

- Host is up (latency 0.011s).
- All 1000 scanned ports were in ignored states: 1000 closed tcp ports (reset).
- Device type: general purpose, running Linux 2.6.X to 5.X.
- Network distance: 2 hops.
- Scan finished in 1.60 seconds.
- Output was saved to `nmap_scan_results.txt`.



![Combined scan](screenshots/04_combined_scan.png)



### 5. Localhost service scan, -sV (my laptop)
My phone had no open ports, so to get a port to analyse I started the SSH service on my own Ubuntu and scanned my own machine with `nmap -sV localhost`.

- Target: localhost (127.0.0.1)
- Host is up
- 999 closed ports (conn-refused)
- 1 open port: **22/tcp, ssh, OpenSSH 10.2p1 Ubuntu 2ubuntu3.8 (protocol 2.0)**
- Service info: OS Linux
- Scan finished in [fill from your screenshot] seconds.



![Localhost service scan](screenshots/05_localhost_service_scan.png)



## Port analysis

| Port | State | Service | Version | What it does | Security risk |
|---|---|---|---|---|---|
| 22/tcp | open | SSH | OpenSSH 10.2p1 Ubuntu 2ubuntu3.8 | Lets a user log in to the machine remotely over an encrypted connection | Medium |

**Why it is a risk:** SSH gives remote control of the machine. If a user has a weak password, attackers can guess it with brute-force attacks. An outdated OpenSSH version could also have known vulnerabilities.

**How to reduce the risk:**
1. Use strong passwords, or better, SSH key authentication.
2. Disable direct root login.
3. Keep OpenSSH updated.
4. Use a firewall to allow SSH only from trusted addresses.
5. Stop the service when it is not needed (`sudo service ssh stop`).

**Other result:** The scan of my phone (100.75.93.186) had no open ports, which means a very small attack surface.

## Problem I faced
On the second day, Nmap showed "Host seems down" for my phone. The reason was that the private VPN connection between my phone and laptop was not active, and the phone's VPN address had changed. After reconnecting and using the new address (100.75.93.186), the host was up again. This taught me that "host seems down" does not always mean the device is off: it can also mean there is no network route to it, or it blocks ping probes (the `-Pn` option skips this check).

## What I learned
- A closed port means nothing is listening on it. An open port means a service is running and can be reached.
- The `-sV` scan showed the exact software and version (OpenSSH 10.2p1), which attackers also use to look for known weaknesses.
- Nmap options are case-sensitive: `-sV` works, but `-sv` fails.
- A device with no open ports (my phone) is harder to attack than one running services.
- Nmap's OS guess is only approximate when no open port is available.
- Every open service should be secured and kept updated, or turned off if it is not needed.

## Files in this folder
- `README.md`: this report
- `nmap_scan_results.txt`: saved Nmap output
- `screenshots/`: terminal screenshots of all scans