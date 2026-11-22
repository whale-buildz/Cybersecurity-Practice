# HTB Redeemer - Lessons Learned

## 1. Overview

This document records the technical knowledge, practical experience and lessons gained from completing the Hack The Box Redeemer machine.

**Platform:** Hack The Box

**Machine:** Redeemer

**Difficulty:** Very Easy

**Operating System:** Linux

**Primary Service:** Redis 5.0.7

**Status:** Completed

## 2. Technical Skills Developed

### A. Network Reconnaissance

Learned how to use Nmap to discover open ports and identify running services.

Command practised:

```bash
nmap -p- -sV <TARGET_IP>
```

Key takeaway:

Open-port discovery helps identify which services may require further investigation.

### B. Redis Enumeration

Learned how to connect to a remote Redis instance using redis-cli.

Command practised:

```bash
redis-cli -h <TARGET_IP>
```

Key takeaway:

Redis is an in-memory key-value database that can store different types of data.

### C. Redis Information Gathering

Learned how to retrieve server information using:

```redis
INFO
```

Key takeaway:

Server information can reveal useful details about software versions, configuration, memory usage and database statistics.

### D. Database Enumeration

Practised identifying stored keys:

```redis
KEYS *
```

Key takeaway:

Redis keys provide a way to identify the information available in a database.

### E. Data Retrieval

Practised retrieving values:

```redis
GET <KEY>
```

Key takeaway:

The GET command retrieves the value associated with a Redis string key.

### F. Redis Key Inspection

Practised:

```redis
TYPE flag
TTL flag
```

Key takeaway:

- TYPE identifies the data type associated with a key.
- TTL checks how long a key has before expiration.

## 3. New Concepts Learned

The following concepts were explored during the exercise:

1. TCP ports and network services.
2. Service and version detection.
3. Redis databases and key-value storage.
4. Redis authentication and access control.
5. Redis data types.
6. Key expiration and Time To Live (TTL).
7. Information disclosure through insufficiently protected services.

## 4. Challenges Encountered

### A. VPN Connectivity After Reboot

After restarting Parrot OS, the previous HTB VPN connection was lost.

Resolution:

Re-established the VPN connection using the downloaded OpenVPN configuration file.

Verified the VPN interface using:

```bash
ip addr show tun0
```

### B. Target IP Address Changed

The original target IP was:

```text
10.129.106.156
```

After reconnecting and returning to the machine, the target IP had changed to:

```text
10.129.114.226
```

Lesson:

Always verify the current target IP from the HTB dashboard before starting or resuming an exercise.

### C. Initial Connectivity Failure

The original target IP returned:

```text
Destination Host Unreachable
```

Lesson:

An active VPN interface does not automatically guarantee that a particular target machine is reachable.

Target status, IP addresses and routing should be checked independently.

### D. Text Editor Availability

Mousepad was initially unavailable on the system.

Resolution:

Installed Mousepad and used it to create and edit Markdown documentation.

## 5. Security Lessons

The most important security lesson from Redeemer was understanding the risks associated with insufficiently protected Redis services.

A Redis instance that permits unauthorized access may expose sensitive information and potentially allow data manipulation.

Security controls should include:

- Strong authentication.
- Appropriate Redis ACLs.
- Network access restrictions.
- Firewall configuration.
- Least-privilege access.
- Regular software updates.

## 6. Areas for Further Practice

The following topics deserve further exploration:

- Redis configuration and security.
- Redis ACLs and authentication.
- Linux networking and routing.
- Nmap scan options.
- TCP/IP fundamentals.
- Database security.
- Vulnerability assessment and reporting.

## 7. Personal Assessment

Completing Redeemer improved my understanding of basic network reconnaissance, service enumeration and database investigation.

I gained practical experience using Nmap, redis-cli and Linux terminal commands.

I also learned the importance of documenting findings, troubleshooting connectivity problems and understanding the security implications of exposed services.

## 8. Final Outcome

**Machine:** Redeemer

**Result:** Successfully completed.

**Flag:** Successfully retrieved and verified.

**Primary Learning Outcome:** Understanding how insufficiently protected Redis services can expose stored information.

**Next Objective:** Progress to the next Hack The Box Starting Point machine while continuing to improve Linux, networking and penetration-testing fundamentals.