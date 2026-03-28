# Fawn - Hack The Box

## Reconnaissance

- VPN connection established using OpenVPN
- Target reachable via ping
- Nmap scan performed:

```bash
nmap -sV <target_IP>
```

- Port 21 (FTP) identified as open

## Exploitation

- Connected to target using FTP:

```bash
ftp <target_IP>
```

- Logged in using anonymous access:

```text
Username: anonymous
Password: (empty)
```

## Post-Exploitation

- Listed files using:

```bash
ls
```

- Downloaded the flag:

```bash
get flag.txt
```

- Exited FTP:

```bash
exit
```

- Read the flag locally:

```bash
cat flag.txt
```

## What I Learned

- Importance of service enumeration with Nmap
- Basic interaction with FTP services
- Risks of anonymous FTP access
- File retrieval from a remote service
