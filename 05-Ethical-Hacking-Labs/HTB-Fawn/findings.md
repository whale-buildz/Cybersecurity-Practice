# HTB Fawn - Findings

## 1. Executive Summary

The Fawn machine exposed an FTP service running vsftpd 3.0.3 on TCP port 21.

The service permitted anonymous authentication, allowing access to the FTP directory and retrieval of a file named `flag.txt` without a named user account.

The machine was completed after successfully retrieving and submitting the flag to Hack The Box.

## 2. Identified Service

| Property | Result |
|---|---|
| Target IP | 10.129.117.212 |
| Port | 21/tcp |
| Service | FTP |
| Software | vsftpd 3.0.3 |
| Anonymous Login | Allowed |

## 3. Security Finding: Anonymous FTP Access

**Description:**

The FTP server allowed users to authenticate using the anonymous account without providing a normal user account.

**Evidence:**

```text
230 Login successful.
```

The remote directory listing revealed `flag.txt`, which was successfully downloaded.

**Security Impact:**

If anonymous FTP access is not intentionally required and properly restricted, unauthorized users may gain access to files exposed through the FTP service.

Depending on the files and permissions involved, this could result in information disclosure.

## 4. Recommended Remediation

For real-world systems:

1. Disable anonymous FTP access unless there is a legitimate business requirement.
2. Restrict FTP access to authorized users.
3. Apply least-privilege permissions to shared directories.
4. Avoid storing sensitive information in publicly accessible directories.
5. Monitor FTP authentication and file-transfer activity.
6. Prefer secure file-transfer alternatives such as SFTP or FTPS where appropriate.

## 5. Completion Status

- [x] Target connectivity verified
- [x] FTP service identified
- [x] Anonymous authentication confirmed
- [x] Remote directory enumerated
- [x] `flag.txt` retrieved
- [x] Flag accepted by Hack The Box

## Conclusion

Fawn demonstrated how an improperly restricted anonymous FTP configuration can expose files to unauthenticated users.

The exercise reinforced the importance of service enumeration, access-control assessment, and secure file-transfer configuration.