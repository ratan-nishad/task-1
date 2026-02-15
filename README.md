 INTERNSHIP  task  REPORT 1

1. Learn to discover open ports on devices in your local network to understand

To discover open ports on devices in your local network during a pentest, start by identifying live hosts, then scan for open TCP/UDP ports. Here's a step-by-step approach using common tools (assuming you're on Kali Linux or a similar pentest distro with these pre-installed).

1. Network Reconnaissance: Find Live Hosts

Use nmap for host discovery on your local subnet (e.g., 192.168.1.0/24). This pings and scans for common ports to find active devices without a full port scan yet.

sudo nmap -sn 192.168.1.0/24

sudo nmap -sn: Ping scan only (no port scan).
  
Replace 192.168.1.0/24 with your subnet (find it via ip route or ifconfig).
Output shows live IPs, MAC addresses, and vendors (e.g., "192.168.1.10 (Router Manufacturer)").

For stealthier scans or ARP-only (faster on local nets):
 


2. Port Scanning: Find Open Ports

Once you have target IPs (e.g., 192.168.1.10), scan ports. Start basic, escalate as needed.

Quick TCP SYN scan (stealthy, root required):

sudo nmap -sS –sV  192.168.1.10
  
•	-sS: SYN scan (half-open, doesn't complete TCP handshake).
•	-p-: All 65k ports (don't limit to top 1000 unless time-constrained).







