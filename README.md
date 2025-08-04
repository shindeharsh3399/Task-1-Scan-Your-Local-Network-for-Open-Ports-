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

   ![IP Range Detection]( )

4. **Scanned the network** with:
   ```bash
   nmap -sS 192.168.1.0/24
