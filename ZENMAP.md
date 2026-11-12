---

## Zenmap Network Scanning (Local LAN)

Zenmap was used to run a Ping scan (`nmap -sn`) on my local network subnet to find live hosts. IP addresses, MAC addresses and device names are hidden for privacy.

### Task 1: Zenmap installed
Yes. Zenmap was downloaded and installed from the official website (nmap.org).

### Task 2: Local IP address and LAN subnet
- **Local IP address:** hidden for privacy
- **LAN subnet:** 192.168.x.0/24 (last digits hidden)

### Task 3: List of live hosts
Command: `nmap -sn <my-local-subnet>` ("Ping scan")

![](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/4750e493ee73ed62550e9ef3e08124a22c19c78a/Zenmap1.png)

The screenshot shows the live hosts found by the Ping scan. IP addresses, MAC addresses, vendor names and device names are covered for privacy.

### Task 4: Number of live hosts
**2 hosts** were live in my subnet (256 IP addresses scanned).

### Task 5: IP addresses of the live hosts
2 IP addresses were found. They are hidden for privacy.

### Task 6: MAC addresses of the live hosts
MAC addresses were displayed for the live hosts in the Zenmap results (Nmap Output tab). They are hidden for privacy.

### Task 7: Topology
![](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/5f88d0662558bc500190c2c4c2f95290c5aa0f97/Zenmap_2.png)

The screenshot shows the network topology from the scan. All labels are covered for privacy.

**Why it matters:** Host discovery shows which devices are active on a network, which is the first step before scanning them for open ports and services.
