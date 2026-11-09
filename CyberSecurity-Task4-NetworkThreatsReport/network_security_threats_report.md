# Common Network Security Threats

**Name:** Shlok Pandey
Track: Security Analyst, Oasis Infobyte SIP
Task 4: Research Report

## Introduction
Almost everything we do today, from banking to studying, depends on networks. This makes networks a favourite target for attackers who want to steal data, spy on users, or shut down services. This report explains four common network threats, how each one works, a real incident, and how to defend against it.

## 1. DoS / DDoS Attacks
How it works: In a Denial of Service attack, the attacker floods a server with so much traffic that real users cannot get through. In a Distributed DoS (DDoS), the traffic comes from thousands of hacked devices called a botnet.

Real example: In October 2016, the Mirai botnet, made of hacked cameras and routers, attacked the DNS provider Dyn. Sites like Twitter and Netflix became unreachable for many users.

Impact: Website downtime, lost revenue, and loss of customer trust.

Mitigations:
1. Rate limiting to cap requests from a single source
2. A DDoS protection service or CDN that absorbs large traffic
3. Firewalls and traffic filtering to drop malicious packets

## 2. Man-in-the-Middle (MITM) Attacks
How it works: The attacker secretly places themselves between a user and a website, so they can read or change the data passing through. This is common on fake or public Wi-Fi.

Real example: In 2011, the certificate authority DigiNotar was breached and fake certificates were issued for sites like Google. They were used to spy on users, mostly in Iran.

Impact: Stolen passwords, bank details, and private messages.

Mitigations:
1. Use HTTPS everywhere
2. Use a VPN on public Wi-Fi
3. Enable strict certificate validation and HSTS

## 3. IP Spoofing
How it works: The attacker forges the source IP address in packets so the traffic appears to come from a trusted machine.

Real example: In February 2018, GitHub was hit by a record DDoS attack using memcached servers. The attackers spoofed GitHub's IP so the servers sent huge replies to GitHub.

Impact: It hides the attacker's identity and makes large DDoS attacks possible.

Mitigations:
1. Ingress and egress filtering on routers
2. Packet filtering to block impossible source addresses
3. Never trusting an IP address alone for authentication

## 4. DNS Poisoning (Spoofing)
How it works: DNS turns website names into IP addresses. In poisoning, the attacker inserts a fake record into a DNS server's cache, so users typing a real website name land on a fake one.

Real example: In 2008, researcher Dan Kaminsky found a flaw that made DNS cache poisoning much easier, and DNS software worldwide had to be patched.

Impact: Fake login pages that steal credentials and spread malware.

Mitigations:
1. Deploy DNSSEC
2. Keep DNS software updated
3. Use trusted DNS resolvers

## Comparison Table
| Threat | Attack vector | Who is at risk | Difficulty to execute | Ease of mitigation |
|---|---|---|---|---|
| DDoS | Flood of traffic | Websites, servers | Medium | Medium |
| MITM | Insecure network or Wi-Fi | Individual users | Medium | Easy |
| IP Spoofing | Forged source address | Servers, networks | Medium | Medium |
| DNS Poisoning | Fake DNS records | Everyone using that DNS | Hard | Medium |

## Conclusion
1. Keep all systems and DNS software updated.
2. Encrypt traffic everywhere with HTTPS and VPNs.
3. Monitor network traffic so attacks are noticed early.

## References
1. CISA, "Understanding Denial-of-Service Attacks"
2. Krebs on Security, article on the Mirai / Dyn attack
3. GitHub Engineering blog, "February 28th DDoS Incident Report" 
4. NIST publication or glossary on DNSSEC / MITM
