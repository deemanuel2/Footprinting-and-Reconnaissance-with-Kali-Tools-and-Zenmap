## Zenmap Network Scanning (Local LAN)

### Task 1: Zenmap installed
Zenmap was downloaded and installed from the official website (nmap.org).

### Task 2: Local IP address and LAN subnet
- **Local IP address:** [hidden for privacy]
- **LAN subnet:** [192.168.x.0/24, last digits hidden]

![ipconfig output](screenshots/ipconfig.png?raw=true)

### Task 3: List of live hosts
Command: `nmap -sn <my-local-subnet>` (Zenmap "Ping scan" profile)

![Zenmap ping scan](screenshots/zenmap-scan.png?raw=true)

### Task 4: Number of live hosts
**[number] hosts were live** in my subnet.

### Task 5: IP addresses of the live hosts
The live hosts' IP addresses are hidden for privacy. [number] addresses were found, including the router.

### Task 6: MAC addresses of the live hosts
MAC addresses were identified for [number] hosts and are hidden for privacy.

### Task 7: Topology
![Zenmap topology](screenshots/topology.png?raw=true)

**Why it matters:** Host discovery shows which devices are active on a network, which is the first step before scanning them for open ports and services.
