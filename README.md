 INTERNSHIP  task  REPORT 1
 🛰 Task 1: Scan Local Network for Open Ports
🎯 Objective

The objective of this task is to discover devices connected to the local network and identify their open ports in order to understand network exposure and potential security risks.

Network scanning is a fundamental reconnaissance step in cybersecurity. It helps in identifying active systems, running services, and possible entry points that attackers may exploit.
🛠 Tools Used
🔹 Nmap

Nmap is a powerful network scanning tool used to:

discover active devices on a network

identify open ports

detect running services

assist in security assessment

It is widely used by cybersecurity professionals and ethical hackers.
<img width="775" height="689" alt="Screenshot (89)" src="https://github.com/user-attachments/assets/59ae3295-47c6-464d-b2ab-a8dd30ad5793" />


🔌 What is a Port?
A port is a communication endpoint that represents a service running on a system.
A port is a 16-bit number (0-65535) that acts like a "door" or "address label" on a device, telling the operating system which application/service should handle incoming network traffic.
Examples:

Port 80 → web traffic

Port 22 → remote login

Port 443 → secure web traffic

If a port is open, the service is accepting connections.


1. Network Reconnaissance: Find Live Hosts

Use nmap for host discovery on your local subnet (e.g., 10.25.213.237/24). This pings and scans for common ports to find active devices without a full port scan yet.
-sn: Ping scan only (no port scan).
Replace 192.168.1.0/24 with your subnet (find it via ip route or ifconfig). Output shows live IPs, MAC addresses, and vendors (e.g., " 10.25.213.237 (Router Manufacturer)").
For stealthier scans or ARP-only (faster on local nets):
<img width="823" height="126" alt="Screenshot_2026-02-15_06-10-53" src="https://github.com/user-attachments/assets/634536cb-a6c4-4b81-959f-9b202f8570bb" />

2. Port Scanning: Find Open Ports

Once you have target IPs (e.g., 10.25.213.237), scan ports. Start basic, escalate as needed.

Quick TCP SYN scan (stealthy, root required):
<img width="1053" height="520" alt="Screenshot_2026-02-15_06-30-13" src="https://github.com/user-attachments/assets/f0a2a4ba-a772-4a63-b251-d6f390bc20b3" />


