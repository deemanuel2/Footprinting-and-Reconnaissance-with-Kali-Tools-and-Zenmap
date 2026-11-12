# Penetration Testing Report
**Footprinting and Network Scanning Phases**
W2-PM-FINAL | Cybersecurity | Networkwalks

| Field | Detail |
|---|---|
| Name | Emmanuel Opara |
| Program/Batch | B084 |
| Date | 13 November 2026 |
| Modules completed | W2-PM1 (Multiple Kali Tools), W2-PM5 (Zenmap Scanning) |
| Client/Target | 1. networkwalks.com (lab target provided by the course) 2. My own local LAN |
| Permission secured? | [Yes / as provided by the course] |
| Phases covered | Phase 1: Reconnaissance and Footprinting; Phase 2: Scanning and Network Discovery |

---

## 1. Liability Disclaimer
These activities were performed only on a lab target provided by my course and on my own network. The material is for education and research only. Running these tools against systems without the owner's permission may be illegal, and I take no responsibility for misuse of this information.

---

## 2. Introduction
This report covers two Week 2 modules. In the first, I footprinted networkwalks.com using six Kali Linux tools. In the second, I used Zenmap to scan my own local network. Together they show how an attacker moves from gathering public information to mapping live hosts. Each step lists the command, what I observed, and why it matters. Screenshots are in the [project README](README.md).

---

## 3. Tools Used

| Tool | Purpose |
|---|---|
| Kali Linux and Windows | Operating systems used |
| whois | Domain registration details |
| whatweb | Web technologies and server information |
| nslookup | Resolving the domain to an IP address |
| curl -I | HTTP response headers |
| wafw00f | Web application firewall detection |
| dnsrecon | DNS record enumeration |
| Zenmap (Nmap) | Live host discovery on my local subnet |
| Windows CMD (ipconfig) | Identifying my local IP address and subnet |

---

## 4. Activities Performed

### 4.1 Footprinting and Reconnaissance (networkwalks.com)
- **whois:** showed the registrar (GoDaddy), the registration and expiry dates, name servers (HostGator and GoDaddy), and that the owner's details are hidden by a privacy service.
- **whatweb:** showed the site redirects HTTP to HTTPS, runs on Apache, and uses WordPress with the WP Download Manager plugin. It also exposed the server IP.
- **nslookup:** resolved the domain to 192.232.216.135.
- **curl -I:** returned HTTP/2 200, showed a caching layer, and revealed the WordPress REST API path (/wp-json/).
- **wafw00f:** detected a ModSecurity (SpiderLabs) web application firewall.
- **dnsrecon:** found 8 records (SOA, NS, A, MX, TXT and SRV), including an SPF policy, a Google site verification, and cPanel autodiscovery records. It also reported recursion enabled on the name servers.

### 4.2 Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap, and selected Ping Scan to identify active hosts.

The scan covered 256 IP addresses and identified **2 live hosts**. MAC addresses were displayed for the live hosts in the Nmap Output tab. The IP addresses, MAC addresses, vendor names and device names are hidden in my screenshots for privacy.

After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.

---

## 5. Risk Analysis / Impact

| # | Finding | Evidence | Potential impact | Risk |
|---|---|---|---|---|
| 1 | Web technologies exposed | whatweb identified WordPress and a plugin | Attackers can look up known issues for those technologies | Medium |
| 2 | Server IP identifiable | nslookup returned the IP | Gives a direct target for scanning | Low |
| 3 | HTTP technical details exposed | curl showed headers and /wp-json/ | Helps fingerprinting and further enumeration | Low |
| 4 | WAF identifiable | wafw00f detected ModSecurity | Reveals part of the security setup | Low |
| 5 | DNS information exposed | dnsrecon listed DNS, mail and service records; recursion enabled | Helps build an infrastructure profile | Medium |
| 6 | Live hosts visible on the local network | Zenmap found 2 live hosts | Unknown devices could go unnoticed | Low |

These are observations, not confirmed vulnerabilities. No exploitation or vulnerability testing was done. Exposed information alone does not mean a system is vulnerable, and further authorized testing would be needed to confirm any weakness.

---

## 6. Recommendations
- Limit the software and version information shown publicly.
- Keep WordPress, plugins and other software updated.
- Review HTTP headers and remove unnecessary technical details.
- Review DNS records regularly, and disable recursion on public name servers.
- Keep the WAF enabled and tuned.
- Scan your own network regularly and investigate unknown devices.
- Keep network documentation and topology up to date.
- Only run reconnaissance and scanning with proper authorization.

---

## 7. Conclusion
In Week 2, I completed practical footprinting and network scanning. Using only public information, I built a profile of networkwalks.com covering its registration, technologies, IP address, firewall and DNS setup. With Zenmap, I identified the live hosts on my own network. I learned that a lot can be learned about an environment before any exploitation, that findings should be documented clearly with evidence, and that all testing must stay within an authorized scope.
