# HTB Fawn - Lessons Learned

## 1. Reconnaissance

- Learned how to use Nmap to identify open ports and running services.
- Used `-sC` to execute default enumeration scripts.
- Used `-sV` to identify service versions.
- Learned the importance of saving scan results for future reference.

## 2. FTP Fundamentals

- FTP operates on TCP port 21 by default.
- FTP uses separate control and data connections.
- The control connection handles commands, while the data connection handles directory listings and file transfers.
- Learned the difference between active and passive FTP modes.

## 3. Anonymous Authentication

- Anonymous FTP allows access without a normal named user account.
- Nmap identified anonymous login as permitted.
- Confirmed the login through the FTP client.
- Learned that anonymous access can expose files when directory permissions are not properly restricted.

## 4. FTP Enumeration

- Used `ls -lah` to inspect the remote directory.
- Identified the available `flag.txt` file.
- Learned how to interpret FTP response codes, including:
  - `220`: Service ready.
  - `230`: Login successful.
  - `331`: Password required.
  - `226`: Transfer completed.

## 5. File Transfer

- Used the FTP `get` command to retrieve a remote file.
- Verified the downloaded file locally.
- Learned to distinguish between remote file permissions and local file ownership.

## 6. Troubleshooting

- Encountered an FTP timeout during an initial directory-listing attempt.
- Reconnected and successfully retrieved the directory listing.
- Learned that FTP data-channel connectivity can affect directory listings and file transfers.

## 7. Security Lessons

- Anonymous FTP access should be disabled when unnecessary.
- Publicly accessible directories should not contain sensitive files.
- File and directory permissions should follow the principle of least privilege.
- Service enumeration is essential when assessing exposed services.

## 8. Commands Practised

```bash
ping -c 4 10.129.117.212
nmap -sC -sV -oN reconnaissance.txt 10.129.117.212
ftp 10.129.117.212
```

FTP commands:

```text
ls -lah
get flag.txt
quit
```

## 9. Final Reflection

Fawn reinforced the importance of identifying exposed services, investigating authentication configurations, and understanding file permissions.

The machine demonstrated how a seemingly simple configuration issue can expose files to unauthorized users.

**Machine Status:** Completed

**Flag Submission:** Accepted by Hack The Box.