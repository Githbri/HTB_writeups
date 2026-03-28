# Preignition - Hack The Box

## Reconnaissance

- VPN connection established using OpenVPN

- Nmap scan performed:

```bash
nmap -sC -sV <target_IP>
```

### Result

- Port 80 open → HTTP service (Nginx)

---

## Enumeration

- Access the web application:

```
http://<target_IP>
```

- No obvious information found in the page source

---

## Directory Brute Force

- Attempted directory enumeration:

```bash
gobuster dir -u http://<target_IP> -w /usr/share/wordlists/dirbuster/directory-list-1.0.txt
```

- No useful directories discovered

---

## Vulnerability Scanning

- Scan with Nikto:

```bash
nikto -h http://<target_IP>
```

### Result

- Discovered `/admin.php`

---

## Exploitation

- Access admin panel:

```
http://<target_IP>/admin.php
```

- Attempt default credentials:

```text
Username: admin
Password: admin
```

- Successful login

---

## Post-Exploitation

- Flag displayed in admin panel after login

---

## Vulnerability

The application uses default credentials for the admin panel.

---

## Impact

- Unauthorized access to administrative interface
- Potential full control over the application
- Data exposure and system compromise

---

## Remediation

- Remove default credentials
- Enforce strong password policies
- Implement account lockout mechanisms
- Use multi-factor authentication (MFA)

---

## Skills Demonstrated

- Service enumeration with Nmap
- Web application enumeration
- Directory brute forcing (Gobuster)
- Vulnerability scanning (Nikto)
- Exploitation of default credentials
