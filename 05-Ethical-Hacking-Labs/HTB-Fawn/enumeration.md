# HTB Fawn - Enumeration

## Objective
Investigate the FTP service discovered during reconnaissance and determine whether anonymous access permits access to remote files.

## Target
- **IP Address:** 10.129.117.212
- **Service:** FTP
- **Port:** 21
- **Version:** vsftpd 3.0.3

## 1. FTP Connection

Command:

```bash
ftp 10.129.117.212
```

Credentials:
- Username: `anonymous`
- Password: Blank

Result:

```text
230 Login successful.
```

Anonymous authentication was successful.

## 2. Directory Enumeration

Command:

```ftp
ls -lah
```

The FTP server returned the following entries:

| File/Directory | Permissions | Size |
|---|---|---|
| `.` | drwxr-xr-x | 4096 |
| `..` | drwxr-xr-x | 4096 |
| `flag.txt` | -rw-r--r-- | 32 bytes |

### Important Observation

The remote directory contained `flag.txt`, a readable file accessible through the anonymous FTP session.

## 3. File Retrieval

Command:

```ftp
get flag.txt
```

Result:

```text
226 Transfer complete.
32 bytes received
```

The file was successfully downloaded to the local working directory.

## 4. Findings from Enumeration

1. Anonymous FTP authentication was permitted.
2. The remote FTP directory was accessible.
3. A file named `flag.txt` was available.
4. The file could be retrieved without authenticating as a named user.
5. The FTP server supported extended passive mode (EPSV), as shown by the successful directory listing.

## Conclusion

FTP anonymous access provided sufficient permissions to enumerate the remote directory and retrieve the available file. This was the central finding of the enumeration phase.