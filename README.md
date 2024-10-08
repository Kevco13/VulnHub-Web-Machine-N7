# VulnHub-Web-Machine-N7

## Objective

The project aimed to build proficiency in network scanning, web application testing, password cracking, and privilege escalation, utilizing a variety of cybersecurity tools and techniques. By completing this challenge, I sought to demonstrate my ability to apply theoretical knowledge in real-world scenarios, effectively analyze security weaknesses, and implement solutions to overcome them.

## Skills Learned

-**Enumeration**: Identifying open ports and services.
-**Exploitation**: Using vulnerabilities to gain access.
-**Password Cracking**: Decoding and cracking password hashes.
-**Privilege Escalation**: Gaining higher-level access on the system.
-**Web Application Testing**: Analyzing and exploiting web applications.
-**Scripting**: Automating tasks with scripts.

## Tools Used

- **nmap**: Port scanning and service enumeration.
- **gobuster**: Directory brute-forcing.
- **Nikto**: Web server vulnerability scanning.
- **Burp Suite**: Web application security testing.
- **Hydra**: Brute-force password cracking.
- **John the Ripper**: Password hash cracking.


# Penetration Testing Workflow

This guide walks through the process of scanning, enumerating, exploiting, and escalating privileges on a target machine, along with capturing final flags.

## 1. Scan the Machine

Use `nmap` to scan the target machine for open ports and services.

| Command | Description |
|---------|-------------|
| `nmap -sV <target-ip>` | Scans the target machine to identify open ports and running services. |

## 2. Enumerate Web Application

Use **gobuster** to brute-force directories on the web application.

| Command | Description |
|---------|-------------|
| `gobuster dir -u http://<target-ip> -w /path/to/wordlist` | Brute-forces directories on the web application. |

Next, use **Nikto** to scan the web server for vulnerabilities.

| Command | Description |
|---------|-------------|
| `nikto -h http://<target-ip>` | Scans the web server for potential security vulnerabilities. |

## 3. Exploit Web Application

Identify and exploit vulnerabilities within the web application. You can use tools like **Burp Suite** for manual inspection and exploitation.

---

## 4. Brute Force Login

Use **Hydra** to brute-force login credentials via an HTTP POST request.

| Command | Description |
|---------|-------------|
| `hydra -l <username> -P <password-list> http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect"` | Attempts brute-forcing the login page with a wordlist. |

## 5. Crack Passwords

Use **John the Ripper** to crack password hashes.

| Command | Description |
|---------|-------------|
| `john --wordlist=/path/to/wordlist /path/to/hashfile` | Cracks password hashes using a provided wordlist. |

## 6. Privilege Escalation

Find and exploit a vulnerability to gain **root access**. Common techniques include searching for binaries with the SUID bit set or exploiting known vulnerabilities in misconfigured services.

## 7. Capture Flags

Finally, locate and read the flags within user home directories and the root directory.

| Command | Description |
|---------|-------------|
| `cat /home/user/flag.txt` | Reads the user flag from the home directory. |
| `cat /root/flag.txt` | Reads the final flag from the root directory. |
