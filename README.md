# port-scan-nmap
Network port scanning using Nmap to identify open ports and assess local network exposure

## Tools Used
- Nmap (https://nmap.org/)
- Wireshark (optional, https://wireshark.org/)

## Steps to Perform the Scan
1. Install Nmap from the official website.
2. Find your local IP range (e.g., `192.168.1.0/24`).
3. Run the following command to perform a TCP SYN scan:
   --> nmap -sS 192.168.1.0/24
4. Note down IP addresses and open ports found.
5. (Optional) Analyze packet capture using Wireshark.
6. Research common services running on discovered ports.
7. Identify potential security risks from open ports.
8. Save scan results as a text or HTML file.

## Sample Scan Results
![image](https://github.com/user-attachments/assets/292fd03b-b201-4851-97d1-5bcd2221ac27)

## Key Concepts
- Port scanning
- TCP SYN scan
- IP ranges
- Network reconnaissance
- Open ports and network security basics


## Interview Questions
**Overview: Open Ports and Scanning Concepts**

**1. What is an open port?**
An open port is a communication endpoint on a device that is actively listening for incoming network traffic. It indicates that a specific service or application is running and waiting for connections. Open ports are essential for network communication but can be exploited if not secured.

**2. How does Nmap perform a TCP SYN scan?**
A TCP SYN scan (using `nmap -sS`) is a stealthy method used by Nmap to determine which ports are open. It sends a SYN (synchronize) packet to the target port:

* If a SYN-ACK is received, the port is **open**.
* If a RST (reset) is received, the port is **closed**.
* If there is no response or an ICMP unreachable message, the port is **filtered**.
  Nmap doesn't complete the TCP handshake, making this scan less detectable.

**3. What risks are associated with open ports?**
Open ports can expose services to attackers. Risks include:

* Unauthorized access to services (e.g., SSH, MySQL)
* Exploitation of known vulnerabilities (e.g., SMB on port 445)
* Information leakage (e.g., NetBIOS on port 139)
* Entry points for malware and worms

**4. Explain the difference between TCP and UDP scanning.**

* **TCP Scan**: Involves establishing a connection (or a partial handshake). It's more reliable because TCP confirms packet delivery.
* **UDP Scan**: Sends a UDP packet and waits for a response. If there’s no reply, the port is assumed open|filtered. UDP scanning is slower and less reliable but can detect services not using TCP.

**5. How can open ports be secured?**

* Close unused ports and disable unneeded services
* Use strong passwords for services that must be open
* Restrict access using firewalls or IP whitelisting
* Bind services to localhost (`127.0.0.1`) when external access isn't needed
* Keep all services and OS updated

**6. What is a firewall's role regarding ports?**
A firewall monitors and controls incoming and outgoing network traffic. Regarding ports:

* It can **block or allow** traffic based on port number, IP, or protocol
* Prevents unauthorized access to open ports
* Acts as a barrier between a trusted internal network and untrusted networks

**7. What is a port scan and why do attackers perform it?**
A port scan is the process of sending packets to a range of ports to determine which ones are open. Attackers perform port scans to:

* Discover active devices and services
* Identify vulnerabilities and entry points
* Map out the network for further exploitation

**8. How does Wireshark complement port scanning?**
Wireshark captures and analyzes real-time network traffic. It complements Nmap by:

* Showing detailed packet-level behavior of port scans
* Identifying which services respond to scan packets
* Helping diagnose abnormal or suspicious traffic during scanning
* Providing visibility into the actual communication on open ports
