# HTB Meow - Findings

## Finding 1: Unauthenticated Remote Root Access Through Telnet

### Description
The target exposed a Telnet service on TCP port 23.

During testing, a connection to the service was established and
the root username was accepted without requiring a password.

This resulted in a successful remote root shell.

### Evidence
- Target: 10.129.116.6
- Port: 23/tcp
- Service: Linux telnetd
- Username: root
- Password: Blank
- Successful shell prompt: root@Meow:~#

### Security Impact
An unauthenticated remote user could obtain administrative access
to the machine.

Potential consequences include:
- Unauthorized access to sensitive information.
- Unauthorized modification or deletion of files.
- Changes to system configuration.
- Disruption of system availability.

Telnet also transmits session data without encryption, creating
additional interception risks.

### Severity
Critical in the context of this lab because remote administrative
access was obtained without password authentication.

This is a lab assessment, not a formal CVSS rating.

### Recommendations
1. Disable Telnet and use SSH for remote administration.
2. Require strong authentication for privileged accounts.
3. Prevent direct remote root login.
4. Restrict administrative access to trusted networks.
5. Apply appropriate firewall rules.
6. Monitor authentication attempts and remote access activity.

## Finding 2: Sensitive File Accessible Through Root Access

### Description
The file flag.txt was found in the root user's home directory.

The file was readable after obtaining root access.

### Evidence
Commands:
ls -la
cat flag.txt

### Impact
Sensitive information stored on the system could be exposed
to anyone who obtained the same level of access.

### Recommendation
Apply least-privilege access controls and protect sensitive
files from unauthorized users.
