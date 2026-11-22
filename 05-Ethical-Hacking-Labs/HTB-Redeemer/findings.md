# HTB Redeemer - Security Findings

## 1. Executive Summary

During the assessment of the Hack The Box Redeemer machine, an exposed Redis service was discovered on TCP port 6379.

The Redis instance permitted connections without authentication, allowing access to its database and the information stored within it.

Four database keys were identified, and their associated values were successfully retrieved.

This demonstrated a security weakness involving insufficient access control on an exposed database service.

## 2. Identified Vulnerability

### Finding 01: Unauthenticated Redis Access

**Vulnerability:** Redis accessible without authentication.

**Affected Service:** Redis 5.0.7

**Affected Port:** TCP 6379

**Severity:** High (in the context of this lab)

### Description

The Redis service accepted a remote connection without requiring authentication.

After connecting using `redis-cli`, it was possible to execute Redis commands and retrieve information from database 0.

The following command successfully established the connection:

```bash
redis-cli -h 10.129.114.226
```

No password was requested.

### Evidence

The following Redis commands were successfully executed:

```redis
INFO
KEYS *
GET flag
TYPE flag
TTL flag
```

The `KEYS *` command revealed four database keys:

- stor
- numb
- flag
- temp

The `GET` command successfully retrieved the values associated with these keys.

The `flag` key contained the correct challenge value.

## 3. Security Impact

An exposed Redis service without appropriate authentication and network restrictions can introduce several security risks.

Potential consequences include:

- **Sensitive information disclosure:** An unauthorized party may retrieve information stored in the database.
- **Data manipulation:** Depending on permissions and configuration, an unauthorized party may modify or delete stored data.
- **Service disruption:** Unauthorized commands could affect database availability or integrity.

The actual impact depends on the data stored, Redis configuration and the level of access available.

## 4. Root Cause

The primary security weakness observed was insufficient access control.

The Redis instance allowed remote access without requiring authentication.

Additionally, the service was reachable over the network from the attacker's lab environment.

## 5. Recommended Remediation

The following measures are recommended for securing Redis deployments:

### A. Enable Authentication

Configure Redis authentication using an appropriate access-control policy.

Where supported, use Redis Access Control Lists (ACLs) to assign users only the permissions they require.

### B. Restrict Network Access

- Bind Redis to trusted interfaces.
- Use firewall rules to restrict access to trusted hosts.
- Avoid exposing Redis directly to untrusted networks or the public internet.

### C. Apply Least Privilege

Create Redis users with only the commands and key access they require.

Avoid granting unnecessary administrative privileges.

### D. Secure Network Communications

Use TLS where appropriate to protect Redis connections against interception.

### E. Maintain Software Updates

Keep Redis updated to a supported version and apply relevant security patches.

## 6. Overall Assessment

The Redeemer exercise demonstrated how insufficiently protected Redis services can expose stored information to unauthorized users.

The successful retrieval of the database contents confirmed the information-disclosure risk in this controlled environment.

Appropriate authentication, network restrictions and access-control policies would significantly reduce this exposure.

## 7. Finding Status

**Status:** Successfully identified and documented.

**Lab:** Hack The Box - Redeemer

**Assessment Type:** Controlled penetration-testing exercise