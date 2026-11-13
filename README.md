# OIBSIP
# Task 2: Basic Firewall Configuration with UFW

**Name:** Shlok Pandey
**Track:** Security Analyst | Oasis Infobyte SIP
**Task:** Basic Firewall Configuration with UFW

## What is a firewall?
A firewall is a security filter between a device and the network. It checks each connection against a set of rules and decides whether to allow or block it. This keeps unwanted traffic out while letting trusted traffic in.

## What is UFW?
UFW (Uncomplicated Firewall) is the simple firewall tool on Ubuntu. It makes it easy to write rules without learning the complex iptables commands.

## Lab setup
| Item | Details |
|---|---|
| Computer | ASUS Vivobook, Windows 11 |
| Linux environment | Ubuntu on Windows Subsystem for Linux (WSL) |
| Tool | UFW |
| Date | 2026-11-13 |

## Steps performed
1. **Install UFW:** `sudo apt install ufw`
2. **Enable UFW:** `sudo ufw enable`
3. **Allow SSH (port 22):** `sudo ufw allow ssh`
4. **Deny HTTP (port 80):** `sudo ufw deny http`
5. **Deny HTTPS (port 443):** `sudo ufw deny https`
6. **Deny one IP address:** `sudo ufw deny from 100.122.127.107`
7. **Check the rules:** `sudo ufw status verbose`

## Rules and why I chose them
| Rule | What it does | Why I chose it |
|---|---|---|
| `allow ssh` (22/tcp) | Allows remote login | Keeps remote management possible |
| `deny http` (80/tcp) | Blocks unencrypted web traffic | HTTP sends data in plain text, so it is risky |
| `deny https` (443) | Blocks encrypted web traffic | Shows how a second web port is closed on a machine that does not host a website |
| `deny from 100.122.127.107` | Blocks all traffic from this address | Shows how one unwanted address can be blocked |

Each rule was added for both IPv4 and IPv6 ("Rule added" and "Rule added (v6)").

## Screenshot: rules and status
The screenshot shows my rule commands and the output of `sudo ufw status verbose`.



![UFW rules and status](screenshots/01_ufw_rules_and_status.png)



Observed output:
- Status: **active**
- Logging: on (low)
- Default policy: **deny (incoming), allow (outgoing), disabled (routed)**
- Rule list: 22/tcp ALLOW IN from Anywhere; 80/tcp DENY IN from Anywhere; 443 DENY IN from Anywhere; DENY IN from 100.122.127.107; and the matching IPv6 (v6) rules.
- When I ran `sudo ufw allow ssh`, UFW said "Skipping adding existing rule" because the SSH rule already existed.

## Testing the denied traffic
Method: I started a simple web server on port 80 with `sudo python3 -m http.server 80`. My first attempt without sudo failed with "Permission denied", because port 80 is a protected port. I then opened `http://172.21.161.151` (my Ubuntu's address) in my Windows browser.

Result: The page did not load. Chrome showed "This site can't be reached" with the error **ERR_CONNECTION_TIMED_OUT**. This shows the firewall dropped the traffic to port 80, as my deny rule says.



![Test result](screenshots/02_test_result.png)



## The script
All commands are saved in `ufw_configuration.sh`. The same rules can be applied again with:
`sudo bash ufw_configuration.sh`

## What I learned
- A firewall matches traffic against rules and allows or blocks it.
- The default policy "deny incoming" means anything not explicitly allowed is blocked.
- Opening only the ports that are needed reduces the attack surface.
- Ports below 1024, like 80, need admin rights (sudo) to use.
- A blocked connection does not reply, so the browser waits and shows a timeout.
- A rule should be tested, because it may not behave the same in every environment.

## Files in this folder
- `README.md`: this report
- `ufw_configuration.sh`: script that applies all rules
- `screenshots/`: screenshots of the rules, status and test