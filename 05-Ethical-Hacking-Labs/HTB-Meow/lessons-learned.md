# HTB Meow - Lessons Learned

## Machine Overview
- Platform: Hack The Box
- Machine: Meow
- Target: 10.129.116.6
- Operating System: Ubuntu 20.04.2 LTS
- Service investigated: Telnet

## Skills Practised

### 1. VPN Verification
Used:
ip addr show tun0

Learned how to verify that the HTB VPN interface is active.

### 2. Network Reconnaissance
Used:
nmap -sC -sV -oN reconnaissance.txt 10.129.116.6

Learned how to identify open ports, discover services and
save scan results.

### 3. Telnet Enumeration
Used:
telnet 10.129.116.6 23

Learned how Telnet provides remote terminal access and why
unencrypted remote administration is insecure.

### 4. Linux Authentication and Privileges
Observed that the root account accepted a blank password.

Learned that root is the Linux superuser and has extensive
administrative privileges.

### 5. Linux File System Navigation
Used:
ls -la
cat flag.txt

Learned how to list files, identify hidden entries and read
a text file.

## Security Lessons
- Exposed services should be carefully assessed.
- Telnet is unsuitable for secure remote administration.
- Privileged accounts must require proper authentication.
- Remote root access should be restricted.
- Sensitive files should be protected using least privilege.

## Completion Status
- [x] VPN connection established
- [x] Initial Nmap scan completed
- [x] Telnet service identified
- [x] Root access obtained
- [x] Flag retrieved
- [x] Flag accepted by Hack The Box

## Final Reflection
Meow demonstrated how a poorly secured remote administration
service can expose an entire Linux system.

The exercise introduced basic network reconnaissance,
service enumeration, remote access and Linux file navigation.
