# Snort-and-Firewall-Rules

# Snort and Firewall Rules Lab

## Overview
This lab demonstrates how a Network Intrusion Detection System (Snort) and a Linux firewall (iptables) work together to detect and block malicious network traffic. A malware file hosted on a simulated web server was downloaded, detected by Snort, and later blocked using firewall rules.

## Objectives
- Configure the Security Workstation virtual machine.
- Monitor IDS alerts with Snort.
- Capture malicious traffic using tcpdump.
- Analyze IDS alert information.
- Configure iptables firewall rules.
- Verify firewall blocks malicious traffic.

## Technologies Used
- Oracle VirtualBox
- Mininet
- Snort IDS
- iptables
- tcpdump
- wget
- netstat
- Linux

## Key Commands
```bash
sudo ./lab.support.files/scripts/cyberops_extended_topo_no_fw.py
./lab.support.files/scripts/start_snort.sh
tail -f /var/log/snort/alert
netstat -tunpa
wget 209.165.202.133:6666/W32.Nimda.Amm.exe
tcpdump -i H5-eth0 -w nimda.download.pcap &
iptables -L -v
iptables -I FORWARD -p tcp -d 209.165.202.133 --dport 6666 -j DROP
```

## Results
- Snort detected the malware download and generated an IDS alert.
- The alert identified the source/destination IP addresses and ports.
- Network traffic was captured into a PCAP file for forensic analysis.
- An iptables rule successfully blocked future connections to the malicious server.
- The malware download failed after the firewall rule was applied.

## Skills Demonstrated
- Intrusion Detection System (IDS) monitoring
- Firewall rule configuration
- Network traffic analysis
- Packet capture using tcpdump
- Linux command-line administration
- Security event investigation
- Incident response fundamentals

## Outcome
Successfully detected malicious network activity with Snort, analyzed captured traffic, and mitigated the threat by implementing an iptables firewall rule to block access to the malicious server.
