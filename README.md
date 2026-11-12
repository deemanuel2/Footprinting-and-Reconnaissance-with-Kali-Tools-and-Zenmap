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

### 1. whois
**Command:** `whois networkwalks.com`
**Purpose:** Domain registration details
