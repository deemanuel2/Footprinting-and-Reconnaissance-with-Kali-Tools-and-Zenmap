## Zenmap Network Scanning (Local LAN)

Zenmap was used to run a Ping scan (`nmap -sn`) on my local network subnet to find live hosts. IP addresses and device names are hidden for privacy.

### Task 1: Zenmap installed
Yes. Zenmap was downloaded and installed from the official website (nmap.org).

### Task 2: Local IP address and LAN subnet
- **Local IP address:** hidden for privacy
- **LAN subnet:** 192.168.x.0/24 (last digits hidden)

### Task 3: List of live hosts
The live hosts found by the Ping scan are shown in the host list in the screenshot under Task 7.

### Task 4: Number of live hosts
**18 hosts** were live in my subnet (256 IP addresses scanned).

### Task 5: IP addresses of the live hosts
18 IP addresses were found. They are hidden for privacy.

### Task 6: MAC addresses of the live hosts
No MAC addresses were displayed in the Zenmap results. Nmap reads MAC addresses through ARP, which depends on Npcap and administrator rights, so they were not shown in this scan.

### Task 7: Topology
![Zenmap topology](https://github.com/deemanuel2/FOOTPRINTING-AND-RECONNAISSANCE-ATTACKS-WITH-MULTIPLE-KALI-TOOLS/blob/34c89b43ddc25bf36c3157774e73efd05865fbf6/Zenmap.png)

The screenshot shows the live host list and the network topology. All IP addresses and device names are covered.

**Why it matters:** Host discovery shows which devices are active on a network, which is the first step before scanning them for open ports and services.
