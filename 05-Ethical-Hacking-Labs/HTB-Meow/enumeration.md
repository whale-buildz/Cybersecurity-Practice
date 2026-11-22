# HTB Meow - Enumeration

## Objective
Investigate the exposed Telnet service and determine whether remote access is possible.

## Service Identified
- Port: 23/tcp
- Service: Telnet
- Version identification: Linux telnetd

## Telnet Connection

Command:
telnet 10.129.116.6 23

Result:
- Connection successful.
- Telnet displayed a login prompt.
- Login prompt: Meow login:

## Authentication Test

Username supplied:
root

Password:
Blank (Enter pressed without entering a password).

Result:
Authentication succeeded.

## Access Details
- Account: root
- Hostname: Meow
- Operating System: Ubuntu 20.04.2 LTS
- Privilege level: Root

Shell prompt:
root@Meow:~#

## Directory Enumeration

Command:
ls -la

Observations:
- Current directory: /root
- A file named flag.txt was present.
- The file was owned by root.

## Flag Retrieval

Command:
cat flag.txt

Result:
The flag was displayed successfully.

## Conclusion
The Telnet service allowed remote root access without a password.
This provided access to the root user's home directory and the machine's flag.
