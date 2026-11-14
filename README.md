# OIBSIP
# OIBSIP: Oasis Infobyte Student Internship Program

**Name:** Shlok Pandey
**Track:** Security Analyst (Cyber Security)
**Organisation:** Oasis Infobyte

This repository contains all my task submissions for the Oasis Infobyte internship. Each task has its own folder with a README, source files or reports, and screenshots.

## Completed tasks

| # | Task | Type | Folder |
|---|---|---|---|
| 1 | Basic Network Scanning with Nmap | Practical | [Open Task 1](CyberSecurity-Task1-NMapScanning/) |
| 2 | Basic Firewall Configuration with UFW | Practical | [Open Task 2](CyberSecurity-Task2-UFWFirewall/) |
| 4 | Research Report: Common Network Security Threats | Research report | [Open Task 4](CyberSecurity-Task4-NetworkThreatsReport/) |
| 6 | Research Report: The Importance of Patch Management | Research report | [Open Task 6](CyberSecurity-Task6-PatchmanagementReport/) |

## Task summaries

### Task 1: Basic Network Scanning with Nmap
I installed Nmap on Ubuntu (WSL) and scanned my own phone and my own laptop. The scans covered basic port scanning, service version detection and OS detection. My laptop showed SSH (port 22) open, which I analysed for security risk.
- [README](CyberSecurity-Task1-NMapScanning/README.md)
- [Scan results file](CyberSecurity-Task1-NMapScanning/nmap_scan_results.txt)

### Task 2: Basic Firewall Configuration with UFW
I installed and enabled the UFW firewall and wrote rules to allow SSH, deny HTTP and HTTPS, and block one IP address. I verified the rules with `ufw status verbose` and tested that traffic to port 80 timed out.
- [README](CyberSecurity-Task2-UFWFirewall/README.md)
- [Configuration script](CyberSecurity-Task2-UFWFirewall/ufw_configuration.sh)

### Task 4: Research Report on Network Security Threats
A report covering DoS/DDoS, Man-in-the-Middle, IP spoofing and DNS poisoning, with real examples, impacts, mitigations and a comparison table.
- [Report](CyberSecurity-Task4-NetworkThreatsReport/network_security_threats_report.md)

### Task 6: Research Report on Patch Management
A report explaining the patch management lifecycle, CVEs and CVSS, real breaches caused by unpatched systems (WannaCry and Equifax), best practices and challenges.
- [Report](CyberSecurity-Task6-PatchmanagementReport/patch_management_report.md)

## Tools and technologies
Nmap, UFW, Ubuntu on WSL, Kali Linux, VirtualBox, Git and GitHub, Markdown.

## Ethics
All scans and tests were done only on devices I own. Scanning or testing systems without permission is illegal.

## Contact
- LinkedIn: https://www.linkedin.com/in/shlok-pandey-4902a83a2?utm_source=share_via&utm_content=profile&utm_medium=member_android
- GitHub: [majorsandeep11](https://github.com/majorsandeep11)

#oasisinfobyte #cybersecurity #internship
