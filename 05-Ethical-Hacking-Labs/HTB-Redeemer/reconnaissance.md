# HTB Redeemer - Reconnaissance

## 1. Lab Information

- **Platform:** Hack The Box
- **Machine:** Redeemer
- **Difficulty:** Very Easy
- **Operating System:** Linux
- **Category:** Starting Point
- **Target IP:** 10.129.114.226
- **Status:** Completed

## 2. Objective

The objective of this stage was to identify the target's exposed network ports and determine which services were running.

## 3. Initial Reconnaissance

### Nmap Scan

Command executed:

```bash
nmap -p- -sV 10.129.106.156
```

### Command Breakdown

- `nmap`: Network scanning tool.
- `-p-`: Scans all TCP ports.
- `-sV`: Attempts to identify service versions.
- Target IP: The machine being investigated.

### Scan Results

| Port | State | Service | Version |
|---|---|---|---|
| 6379/tcp | Open | Redis | 5.0.7 |

## 4. Initial Observations

- Redis was accessible on TCP port 6379.
- Redis version 5.0.7 was identified.
- No other open TCP ports were reported by this scan.

## 5. Conclusion

The reconnaissance stage identified Redis as the primary exposed service.

Further investigation of the Redis service was required to understand its configuration and accessible data.

## 6. Next Stage

Proceed to service enumeration and investigate the Redis database.
