# Task-1- Scan Your Local Network for Open Ports.

# 🔍 Local Network Port Scanning with Nmap.

## 📘 Description

This project demonstrates how to scan a local network using **Nmap** to find active devices and their open ports. The goal is to identify running services and assess potential security risks within the network.

## 🛠 Tools Used

- [Nmap](https://nmap.org/) – Network scanning tool
- [Zenmap](https://nmap.org/download) - Network scanning tooll for Windows  

## 📡 Steps Followed

1. **Installed Nmap** from the official website.
2. **Found local IP range** using `ipconfig`(Windows) or `ifconfig`(Linux) (e.g., `192.168.1.1/24`).

   ![IP Range Detection](https://github.com/shindeharsh3399/Task-1-Scan-Your-Local-Network-for-Open-Ports-/blob/main/Screenshot%202025-08-04%20164410.png)

3. **Scanned the network with:**
    ```bash
   nmap -sS 192.168.1.1/24
    
4. ## Identified active devices and open ports.
   ![devices and ports](https://github.com/shindeharsh3399/Task-1-Scan-Your-Local-Network-for-Open-Ports-/blob/main/Screenshot%202025-08-04%20161446.png)
   
5. **Looked up services running on open ports.**

   Below are the devices discovered on the local network along with their open TCP ports and known services:

   | IP Address      | Open Ports (TCP)             | Detected Services                          |
   |------------------|-------------------------------|---------------------------------------------|
   | **192.168.1.1**   | 23, 80, 1900                  | Telnet, HTTP, UPnP                          |
   | **192.168.1.104** | 23, 80                        | Telnet, HTTP                                |
   |                  | 53 (filtered)                 | DNS (filtered)                              |
   | **192.168.1.103** | 80, 135, 139, 902, 912        | HTTP, MSRPC, NetBIOS-SSN, RealSecure, Apex-Mesh |
   | **192.168.1.110** | 80, 135, 139, 445, 902, 912   | HTTP, MSRPC, NetBIOS-SSN, Microsoft-DS, RealSecure, Apex-Mesh |

   📌 *Note: Filtered ports may be blocked by firewalls or ACLs and are not fully open.*

6. **Assessed Potential Security Risks**

   Based on the open ports discovered during the scan, here are some potential security concerns:

   | Port | Service        | Risk Description                                                                 |
   |------|----------------|------------------------------------------------------------------------------------|
   | 23   | Telnet         | Unencrypted login protocol. Vulnerable to interception and should be disabled or replaced with SSH. |
   | 80   | HTTP           | Unsecured web traffic. Consider using HTTPS (port 443) to encrypt data in transit. |
   | 445  | Microsoft-DS   | Used for SMB file sharing. Often targeted in ransomware attacks; should be blocked externally. |
   | 135  | MSRPC          | Can be abused for remote execution or DCOM attacks. Limit exposure to local network. |
   | 139  | NetBIOS-SSN    | Old Windows sharing protocol. Should be disabled if not used.                      |
   | 902  | RealSecure     | Unknown/possibly custom or legacy service. Review if required, otherwise close.   |
   | 912  | Apex-Mesh      | Possibly part of a proprietary or IoT service. Validate if it’s needed.            |
   | 1900 | UPnP           | Can expose devices to remote control vulnerabilities. Should be disabled on routers. |

   ### 🔧 Recommendations:

   - Disable unused or unknown services.
   - Replace Telnet with SSH.
   - Use a firewall to restrict access to ports like 445, 135, and 139.
   - Ensure all devices are updated with the latest firmware and security patches.
   - Use HTTPS where possible for web interfaces.

7. **Saved Results Using**
   The scan results were saved using the `-oN` option in Nmap, which outputs the results in a readable text format.

   ### 📌 Command Used:
   ```bash
      nmap -sS -T5 -oN scan.txt 192.168.1.1/24

- **-sS → TCP SYN Scan**
   Performs a stealthy and fast scan by sending SYN packets to discover open ports without completing the full TCP handshake.

- **-T5 → Aggressive Timing**
   Increases scan speed using the most aggressive timing template. Best used on fast and reliable networks.

- **-oN scan.txt → Output to Text File**
   Saves the scan results in normal, human-readable text format as scan.txt.

8. **📂 Output File**

   **`scan.txt`**:  
   This file contains the detailed results of the network scan, including:

   - IP addresses of active devices  
   - Open ports on each device  
   - Detected services associated with those ports  

   You can view the raw scan results directly in the [`scan.txt`](https://github.com/shindeharsh3399/Task-1-Scan-Your-Local-Network-for-Open-Ports-/blob/main/scan.txt) file

   ## 📚 Resources

   - 🔗 [Nmap Documentation](https://nmap.org/book/)  
     Official guide to using Nmap, including command options, scan types, output formats, and more.

   - 🔢 [Common Ports List (Wikipedia)](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)  
     A comprehensive list of well-known TCP and UDP port numbers and their associated services.


   ## ✅ Conclusion

   Scanning your local network is a great way to understand what devices and services are running.Using tools like **Nmap** helps you identify open ports, detect        potential vulnerabilities,and take action to secure your network before threats can exploit them.
   Regular scans are a simple but powerful step toward better network security.


   
   
