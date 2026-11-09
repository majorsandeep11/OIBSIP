# The Importance of Patch Management

**Name:** Shlok Pandey
**Track:** Security Analyst | Oasis Infobyte SIP
**Task 6:** Research Report

## Introduction
Patch management is the process of finding, testing, and installing software updates (patches) that fix bugs and security holes. Every piece of software has flaws. When a flaw is found and reported, the vendor releases a patch. From that day, attackers race to exploit the flaw before users update. Systems that stay unpatched become easy targets, which is why patching is one of the most important parts of cybersecurity.

## Why Patches Matter

### How vulnerabilities are tracked
- **CVE (Common Vulnerabilities and Exposures):** A public ID given to each known vulnerability, for example CVE-2017-0144. It lets everyone refer to the same flaw.
- **CVSS (Common Vulnerability Scoring System):** A score from 0 to 10 showing how dangerous a vulnerability is. A higher score means it should be patched sooner.

### Real-world breach 1: WannaCry (May 2017)
WannaCry was ransomware that spread using EternalBlue, a flaw in Windows file sharing (SMB). Microsoft had released the patch (MS17-010) in March 2017, two months before the attack, but many systems were not updated. The attack hit hundreds of thousands of computers in about 150 countries, including hospitals in the UK's NHS, where appointments and operations were disrupted.

### Real-world breach 2: Equifax (2017)
Attackers entered Equifax's systems through a known flaw in Apache Struts (CVE-2017-5638). A patch had been available for months, but the affected system was not updated. The personal data of about 147 million people was exposed, and Equifax later agreed to a settlement of at least $575 million.

## Consequences of Not Patching
- **Data breaches:** Personal and financial data is stolen.
- **Ransomware:** Files are locked and money is demanded.
- **Legal and compliance problems:** Fines under laws and standards such as GDPR and PCI-DSS.
- **Financial loss:** Recovery costs, downtime, and lawsuits.
- **Loss of reputation:** Customers stop trusting the company.

**Statistics:** [Add 2-3 numbers from the IBM "Cost of a Data Breach" report or the Verizon "Data Breach Investigations Report" and name the source next to each number.]

## Patch Management Lifecycle
1. **Discovery:** Make a list of all devices, operating systems, and software the organisation uses.
2. **Assessment:** Check which patches are needed and rank them using CVSS scores and how exposed the system is.
3. **Testing:** Install the patch on a test system first to make sure it does not break anything.
4. **Deployment:** Roll the patch out to real systems, starting with the most critical ones.
5. **Verification:** Confirm that the patch installed correctly and that the vulnerability is closed.

## Best Practices: 7-Step Checklist
1. Keep an up-to-date inventory of all assets.
2. Subscribe to vendor security alerts and CVE feeds.
3. Prioritise patches by severity and exposure.
4. Test every patch before wide deployment.
5. Automate updates wherever possible.
6. Keep a rollback plan in case a patch causes problems.
7. Audit and report on patch status regularly.

## Challenges and How to Overcome Them
| Challenge | How to overcome it |
|---|---|
| Legacy systems that no longer get patches | Isolate them on a separate network and plan to replace them |
| Fear of downtime | Patch during scheduled maintenance windows |
| Testing takes time and effort | Use a small test group first, then automate testing |
| Too many patches to track | Use patch management tools and prioritise by CVSS |

## Conclusion
Most successful attacks use flaws that already have a fix. WannaCry and Equifax both could have been prevented by timely patching. A clear process (discover, assess, test, deploy, verify) turns patching from a risk into a routine habit.

## References
1. NIST, SP 800-40 Rev. 4, "Guide to Enterprise Patch Management Planning"
2. CISA, alert or guidance on the WannaCry ransomware 
3. NIST National Vulnerability Database (NVD), CVE and CVSS information 
4. U.S. Government Accountability Office (GAO), report on the Equifax data breach 
