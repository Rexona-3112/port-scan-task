# port-scan-task
🔍 Cyber Security Internship – Task 1: Local Network Port Scanning

📘 Objective: The objective of this task was to perform basic network reconnaissance by scanning devices within a local network to discover open ports and identify potential security risks. This helps develop a practical understanding of how exposed services can pose security threats if left unprotected.

🧰 Tools Used

- Nmap: A free and open-source utility for network discovery and security auditing.
- Command Line Interface: For running scans and saving output.
- Wireshark: Packet analyzer used to visualize network traffic.

⚙️ Methodology

🔹 Step 1: Install Nmap

Nmap was downloaded and installed from the official website: [https://nmap.org/download.html](https://nmap.org/download.html)

🔹 Step 2: Identify IP Range

Using the `ipconfig` (on Windows), I identified the IPv4 address of my device: 192.168.101.220

IPv4 Address: 192.168.101.220

From this, I inferred the local subnet as:  192.168.101.220


🔹 Step 3: Perform a TCP SYN Scan

Executed the following command in terminal:

nmap -sS 192.168.101.220 > scan_results.txt

* -sS: Performs a stealth TCP SYN scan.
* 192.168.101.220: Scans all devices in the subnet.
* > scan_results.txt: Saves the output to a text file.


📊 Scan Results

Below is a sample of the discovered open ports on one of the scanned devices:

| Port     | State | Service      |
| -------- | ----- | ------------ |
| 135/tcp  | open  | msrpc        |
| 139/tcp  | open  | netbios-ssn  |
| 445/tcp  | open  | microsoft-ds |
| 2179/tcp | open  | vmrdp        |


  🔍 Service Explanation & Risk Analysis

 # ▶️ Port 135 (msrpc)

* Description: Microsoft RPC endpoint mapper. Used for DCOM and other services.
* Risk: Can be exploited for remote code execution.
* Recommendation: Block externally via firewall. Only allow trusted internal access.

 # ▶️ Port 139 (netbios-ssn)

*  Description : Used for Windows file and printer sharing over NetBIOS.
*  Risk : Vulnerable to enumeration attacks and exploits like null sessions.
*  Recommendation : Disable if not using file sharing.

 # ▶️ Port 445 (microsoft-ds)

*  Description : Supports SMB protocol for file sharing and remote access.
*  Risk : Highly targeted by malware (e.g., WannaCry).
*  Recommendation : Disable SMBv1. Restrict access and patch systems regularly.

 # ▶️ Port 2179 (vmrdp)

*  Description : RDP for managing virtual machines (Hyper-V).
*  Risk : Potential for brute-force or remote desktop exploits.
*  Recommendation : Enable RDP only if needed. Use strong passwords and restrict access via firewall or VPN.

  🔐 General Security Recommendations

* 🔒  Close Unused Ports : Disable unnecessary services to reduce attack surface.
* 🧱  Use Firewalls : Block incoming access to sensitive ports from external networks.
* 🔑  Strong Authentication : Use strong, unique passwords and two-factor authentication where possible.
* 🧰  Update Regularly : Patch known vulnerabilities in services and OS.
* 🔍  Monitor Network Activity : Tools like Wireshark or IDS (e.g., Snort) can help detect malicious behavior.
