![image](https://github.com/user-attachments/assets/c2849eeb-bc5b-4bf8-ac3a-e177cdc22a58)

# Virtualized Network Environment on Proxmox

## Overview
This project showcases a basic virtualized network environment created using Proxmox Virtual Environment (PVE). The setup includes core network components like a router, firewall, DNS/DHCP server, and monitoring system. It is designed for learning, testing, and understanding network concepts in a controlled virtual environment.


## Project Components

**Router (Debian):**

  - Acts as a gateway, connecting the internal LAN to the external network (WAN).
  - Configured with NAT (Network Address Translation) and IP forwarding.

**Firewall (pfSense):**

  - Manages and secures traffic between the LAN and WAN.
  - Provides advanced firewall features, such as NAT and filtering.

**DNS/DHCP Server (Pi-hole):**

  - Offers DNS and DHCP services for the internal LAN.
  - Blocks ads and unwanted traffic at the network level.

**Monitoring System (Zabbix):**

  - Monitors the health and performance of devices in the network.
  - Provides a centralized dashboard for managing alerts and metrics.

## Why This Setup?

**The purpose of this project is to:**

  - Create a small-scale network environment for testing and learning.
  - Understand the interaction between core network components.
  - Practice deploying and managing network services in a virtualized environment.

## Network Structure

**Component	Role	IP Address	Software**

- RouterVM	Gateway	192.168.2.1	Debian
- pfSense	Firewall	WAN: 192.168.2.x (DHCP), LAN: 192.168.100.1	pfSense
- Pi-hole	DNS/DHCP Server	192.168.100.2	Debian + Pi-hole
- Zabbix	Monitoring System	192.168.100.3	Debian + Zabbix
- Client	Test Device	DHCP (from Pi-hole)	Any OS

## Setup Summary

  **Proxmox Environment:**
  
  - Installed on a dedicated server.
  - Network bridges:
    - vmbr0: WAN connection.
    - vmbr1: Internal LAN connection.

   **Router (Debian):**
   - Configured with static IPs for WAN and LAN interfaces.
   - Enabled NAT and IP forwarding to route traffic between WAN and LAN.

   **Firewall (pfSense):**
   - Configured WAN and LAN interfaces.
   - DHCP enabled on LAN.

   **DNS/DHCP Server (Pi-hole):**
   - Installed and set up to manage LAN DNS and DHCP.
   - Blocks ads at the network level.

   **Monitoring System (Zabbix):**
   - Tracks the performance of devices in the network.
   - Provides metrics and alerts for monitoring.

## How to Use

   - Connect client devices to the LAN (via vmbr1 or DHCP from Pi-hole).
    Access:
        - pfSense: http://192.168.100.1
        - Pi-hole Dashboard: http://192.168.100.2/admin
        - Zabbix Dashboard: http://192.168.100.3/zabbix

     - Monitor network traffic, manage firewall rules, and test DNS/DHCP services
    
