# HTB Fawn - Reconnaissance

## Target Information
- **Machine:** Fawn
- **Platform:** Hack The Box (Starting Point)
- **Target IP:** 10.129.117.212
- **Date:** 23 November 2026

## Objective
Identify the target's availability, exposed TCP ports, running services, and service versions.

## Connectivity Check
Command:
```bash
ping -c 4 10.129.117.212
```

Result:
- 4 packets transmitted
- 4 packets received
- 0% packet loss
- Average latency: 132.075 ms

## Nmap Scan

Command:
```bash
nmap -sC -sV -oN reconnaissance.txt 10.129.117.212
```

### Scan Results

| Port | State | Service | Version |
|---|---|---|---|
| 21/tcp | Open | FTP | vsftpd 3.0.3 |

### Key Observations

1. The target was reachable during scanning.
2. TCP port 21 was open.
3. The FTP service was identified as vsftpd 3.0.3.
4. Nmap's FTP anonymous-login script confirmed that anonymous FTP access is permitted.
5. The FTP directory listing revealed a file named `flag.txt`.
6. The server identified its operating system as Unix.

## Initial Assessment

The exposed FTP service and permitted anonymous login provide a clear direction for further enumeration.

The presence of `flag.txt` in the FTP listing is an important finding to investigate during the next phase.

## Conclusion

The reconnaissance phase identified FTP as the exposed service and anonymous access as the primary area for further investigation.