# FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS
Footprinting networkwalks.com with Kali Linux tools (whois, whatweb, nslookup, curl, wafw00f, dnsrecon) to build a target profile for later scanning tasks.

---

## Objective
To footprint the website networkwalks.com using Kali Linux tools (whois, whatweb, nslookup, curl, wafw00f, dnsrecon) and gather information about its registration, technologies, DNS records, and security defenses. Zenmap was also used to scan my own local network and identify live hosts. These findings will form the foundation for planning the scanning tasks that follow.

---

## Disclaimer
This project is for educational purposes only and was completed as part of a cybersecurity training course. The footprinting was performed on networkwalks.com, the target used in the course lab, and the Zenmap scan was run only on my own local network. Do not use these tools or techniques against any system without the owner's explicit written permission. Unauthorized scanning or testing may be illegal. The author takes no responsibility for misuse of the information in this repository.

---

## Tools Used
| Tool | Purpose |
|------|---------|
| whois | Domain registration details |
| whatweb | Website technologies and server info |
| nslookup | DNS lookups (IP addresses, mail servers) |
| curl | HTTP headers and server responses |
| wafw00f | Detects web application firewalls |
| dnsrecon | DNS enumeration (A, MX, NS, TXT records) |
| Zenmap (Nmap) | Host discovery (ping scan) and network topology on my local LAN |

---

### whois networkwalks.com
![](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/48be886683a786c4ee231b53756318ea94e3b5ed/whois_result.png)

![](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/48be886683a786c4ee231b53756318ea94e3b5ed/whois2_result.png)

**Findings:** Registrar, creation and expiry dates, name servers, and whether registrant details are hidden by privacy protection.

**Why it matters:** Registration details show who manages the domain and which name servers it uses. They can reveal how long the site has existed and who could be contacted about it.

---

### whatweb networkwalks.com
![]()

**Findings:** Web server, CMS (for example WordPress), programming language, plugins, and versions detected.

**Why it matters:** Knowing the technologies and versions in use helps an attacker look for known weaknesses, and helps a defender see what information the site gives away.
