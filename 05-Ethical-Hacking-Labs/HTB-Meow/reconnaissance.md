# HTB Meow - Reconnaissance

## Lab Information
- Platform: Hack The Box
- Machine: Meow
- Target IP: 10.129.116.6
- Operating System: Ubuntu 20.04.2 LTS
- Difficulty: Very Easy

## Objective
Identify the target host and discover exposed network services.

## VPN Verification
Command:
ip addr show tun0

Result:
- VPN interface: tun0
- VPN IPv4: 10.10.17.91/23
- Interface state: UP

## Nmap Scan

Command:
nmap -sC -sV -oN reconnaissance.txt 10.129.116.6

### Results

| Port | State | Service | Version |
|---|---|---|---|
| 23/tcp | Open | Telnet | Linux telnetd |

Additional observations:
- Host was reachable.
- 999 of the 1,000 scanned TCP ports were closed.
- Operating system information identified Linux.

## Initial Assessment
Telnet was the only open service identified in the initial scan.

Telnet provides remote terminal access and does not encrypt session traffic.

## Evidence
The complete Nmap output is saved in reconnaissance.txt.
