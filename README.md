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

**Findings:** 
- Registrar: GoDaddy.com, LLC.
- Registered on 2019-11-06, last updated 2025-11-12, and expires 2027-11-06.
- The owner's details are hidden behind a privacy service (Domains By Proxy, LLC).
- Name servers belong to HostGator (NS6135/NS6136) and GoDaddy (NS29/NS30.DOMAINCONTROL.COM).
- Transfer, update, renew and delete locks are set, and DNSSEC is unsigned.

**Why it matters:** Registration details show who manages the domain and which name servers it uses. They can reveal how long the site has existed and who could be contacted about it.

---

### whatweb networkwalks.com
![](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/c3b835b419b2efa9e103bf4e924731513c2b24e6/whatweb.png)

**Findings:**
- HTTP is redirected (301) to HTTPS.
- Runs on an Apache web server with WordPress and the WP Download Manager plugin.
- Also uses jQuery, Google Tag Manager and HTML5.
- Exposes the server IP (192.232.216.135) and a contact email.
- Sets a session cookie with the HttpOnly flag.

**Why it matters:** Knowing the technologies and versions in use helps an attacker look for known weaknesses, and helps a defender see what information the site gives away.

---

### nslookup networkwalks.com
![](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/f5980abdd02cb188d0dbeb0fabded686f941e5cb/nslookup.png)

**Findings:** 
- The domain resolves to 192.232.216.135 (non-authoritative answer).
- The answer came from my lab network's DNS server.

**Why it matters:** The IP address shows where the site is hosted and gives a target for later scanning. Mail servers show how the domain handles email.

---

### curl -I https://networkwalks.com
![](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/f5980abdd02cb188d0dbeb0fabded686f941e5cb/Screenshot_2026-11-11_16-25-57.png)

**Findings:** 
- Returns HTTP/2 200, with Apache as the server.
- A caching layer sits in front of WordPress.
- The link header reveals the WordPress REST API (/wp-json/).
- The session cookie has the Secure and HttpOnly flags.
  
**Why it matters:** HTTP headers reveal the server software and show whether protections such as HSTS or content security policies are in place.
**Why it matters:** The IP address shows where the site is hosted and gives a target for later scanning. Mail servers show how the domain handles email.

---

### wafw00f https://networkwalks.com
![wafw00f output](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/f5980abdd02cb188d0dbeb0fabded686f941e5cb/wafwoof.png)

**Findings:** 
- The site is protected by a ModSecurity (SpiderLabs) web application firewall.
- Detected in 2 requests.

**Why it matters:** A WAF can block or alter scanning and attack attempts, so knowing about it helps plan later tasks and shows how well the site is defended.

---

## dnsrecon -d networkwalks.com
![dnsrecon output](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/f5980abdd02cb188d0dbeb0fabded686f941e5cb/dnsrecon.png)

**Findings:** 
- 8 records found: SOA, NS, A, MX, TXT and SRV.
- The A record and mail server (mail.networkwalks.com) both point to 192.232.216.135.
- TXT records include an SPF policy and a Google site verification.
- SRV records support cPanel email autodiscovery.
- Recursion was reported as enabled on the name servers, and no DNSSEC answer was returned.

**Why it matters:** DNS records map out the domain's infrastructure. Extra subdomains or TXT records (such as SPF) can reveal additional services and how email is protected.
