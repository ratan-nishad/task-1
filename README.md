 INTERNSHIP  task 1 Scan Local Network
 
 🛰 Scan Local Network for Open Ports
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

📌 Discovered Devices and Open Ports

After scanning the local network, multiple active devices were identified along with their open ports and running services.

🖥 Detected Hosts
🔹 Device 1: Router / Gateway

IP Address: 10.25.213.237
Open Ports:

53 → DNS service

80 → Web management interface

443 → Secure web interface

Explanation:
This device is likely the network router. Open ports 80 and 443 indicate a web-based configuration panel. Port 53 is used for domain name resolution.

🔹 Device 2: Local Computer

IP Address: 10.25.213.232
Open Ports:

135 → Windows RPC

445 → SMB file sharing

3389 → Remote Desktop Protocol (RDP)

Explanation:
These ports indicate a Windows machine. SMB enables file sharing, while RDP allows remote desktop access.

🔹 Device 3: Mobile Device

IP Address:  10.25.213.173
Open Ports:

No significant open ports detected

Explanation:
Most mobile devices block incoming connections for security reasons.
<img width="1270" height="772" alt="Screenshot_2026-02-15_06-29-49" src="https://github.com/user-attachments/assets/d0cd50ba-0ebd-4818-97ea-8595a4a8c078" />

📡 Optional Analysis: Packet Capture Using Wireshark
🎯 Objective

The purpose of packet capture analysis is to observe and understand the network traffic generated during the port scanning process. This helps in identifying how scanning works at the packet level and how target systems respond.

🧠 What is Packet Capture?

Packet capture is the process of recording network traffic in real time.
Each piece of transmitted data is called a “packet.”

By analyzing packets, we can see:

source IP address

destination IP address

protocol used (TCP, UDP, etc.)

port numbers

response from target devices

🔎 Observations During Port Scanning

While analyzing the packet capture during the scan, the following behavior was observed:

✔ SYN Packets Sent

The scanning machine sends TCP SYN packets to multiple ports on target devices.

This indicates the beginning of a TCP handshake.

✔ SYN-ACK Response (Open Port)

If a port is open:

The target responds with a SYN-ACK packet.

This confirms the port is accepting connections.

✔ RST Response (Closed Port)

If a port is closed:

The target responds with a RST (Reset) packet.

This indicates the port is not accepting connections.

✔ No Response (Filtered Port)

If a firewall blocks the traffic:

No reply is received.

This indicates the port may be filtered.
<img width="1280" height="605" alt="Screenshot_2026-02-15_08-38-39" src="https://github.com/user-attachments/assets/1e2704b2-fa56-40b7-8307-8e82b6ccd3bd" />

7. Identify Security Risks

High Risk Ports:

  22 (SSH): Brute force attacks if weak passwords; key-based auth recommended
  23 (Telnet): Unencrypted credentials - immediate disable
  445 (SMB): EternalBlue/MS17-010 vulnerability if unpatched
  3389 (RDP): BlueKeep vulnerability, weak passwords
  Database ports (3306, 1433): Exposed to internet = data breach risk

Medium Risk:

  80/443: Vulnerable web apps (SQLi, XSS, RCE)
  8080: Often development servers with weak auth

  Interview Questions:

1️⃣ What is an open port?
 An open port is a network endpoint that accepts incoming connections.

2️⃣ How does Nmap SYN scan work?
 It sends a SYN packet without completing the TCP handshake to detect port status.

3️⃣ Risks of open ports?
 Unauthorized access, vulnerabilities, and malware entry points.

4️⃣ Difference between TCP and UDP scan?
 TCP is reliable and fast; UDP is slower and connectionless.

5️⃣ Firewall role?
 It filters ports and blocks unauthorized traffic.

6️⃣ Why do attackers scan ports?
 To find weak entry points and vulnerable services.

7️⃣ How does Wireshark help?
 It analyzes network packets to detect suspicious activity.

