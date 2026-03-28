# Local Network Port Scanning



# Task 1 – Local Network Port Scanning

## Objective  
To identify open ports within a local network and assess potential security exposures.

**Date:** 20-10-2025  
**Author:** Charitardha Pulipati  
**Repository:** [https://github.com/Charitardha555/Elevate-labs-Cybersecurity-Task-01]

---

## Tools Used  
- Nmap (required)  
- Wireshark (optional for packet analysis)  

---

## Methodology

1. **Determine local network IP range**  
   Example: 192.168.1.0/24  
   Actual used: 192.168.1.1/24  

2. **Perform a TCP SYN scan using Nmap**  
   Command used:  nmap -sS 192.168.1.1/24


3. **Analyze the output**  
- Number of active hosts: 6  
- List of IPs with open ports: 3  
- Common services detected: 80/tcp (http)

---

## Results Summary

| IP Address  | Open Ports                                | Services                               | Security Risk Level  |
|-------------|------------------------------------------|--------------------------------------|---------------------|
| 192.168.1.1 | 23/tcp filtered, 53/tcp open, 80/tcp open, 443/tcp open | Telnet, domain, http, https           | Medium    |
| 192.168.1.2 | Ports are in ignored state                |                                      | Low                     |
| 192.168.1.3 | Ports are in ignored state                |                                      | Low                    |
| 192.168.1.4 | Ports are in ignored state                |                                      | Low                    |
| 192.168.1.6 | 5555/tcp open, 8008/tcp open, 8009/tcp open, 8010/tcp open, 8443/tcp open, 9000/tcp open | Freeciv, http, ajp13, Xmpp, https-alt, cslistener | High                    |
| 192.168.1.8 | 80/tcp open, 135/tcp open, 139/tcp open, 443/tcp open, 445/tcp open, 2179/tcp open, 3306/tcp open, 3580/tcp open, 5357/tcp open, 16992/tcp open | http, msrpc, netbios-ssn, https, microsoft-ds, vmrdp, mysql, nati-svrloc, Wsdapi, amt-soap-http | High                    |

---

## Analysis  

- 192.168.1.1 has commonly exploited ports (Telnet - 23, DNS, HTTP, HTTPS), thus medium risk due to exposure to common network services.

- 192.168.1.2, 1.3, 1.4 have ports in ignored state which suggests minimal exposure, so low risk.

- 192.168.1.6 shows multiple open ports for various services including admin interfaces (5555/tcp) and secure communication ports—medium to high risk due to potential attack vectors through multiple services.

- 192.168.1.8 has numerous open ports including database (MySQL - 3306), file sharing, and RPC services, which presents a high risk for unauthorized access or lateral movement in network.

The port scan reveals a network with varied exposure levels across devices. While several hosts maintain a low risk profile by employing minimal or ignored ports, others exhibit medium to high risks due to multiple open services that potentially expose administrative, database, and file-sharing functions. The presence of common and often targeted ports — such as Telnet, MySQL, and RPC services — on some IPs elevates the threat landscape, increasing susceptibility to exploitation and unauthorized access. This highlights a need for stringent port management and firewall policies to limit attack surfaces, particularly for critical systems with multiple active services.

---

## Security Recommendations  

- Enable only the required ports.  
- Disable all unused or unwanted ports on systems.  
- Never share your network with unknown or untrusted people.  
- Configure Firewall on the router.  

---


## Files Included  

- 'Task_1_Nmap_scan.txt` — raw scan output  
- Wireshark capture file is not uploaded due to the security reasons
- `README.md` — task documentation (this file)  
- `screenshots/` — evidence of commands & output

---

## Screenshots  
 

![Nmap Scan Screenshot](./screenshots/nmap_scan.png)  
![Wireshark Capture Screenshot](./screenshots/wireshark_capture.png)  

---
