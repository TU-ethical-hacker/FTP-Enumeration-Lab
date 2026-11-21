FTP Enumeration & Anonymous Access Assessment

Project Overview

This project is a hands-on ethical hacking lab performed using Kali Linux and Metasploitable 2. The purpose was to identify an FTP service, check its version, and verify whether anonymous login was enabled.

Lab Environment

- Attacker Machine: Kali Linux
- Target Machine: Metasploitable 2
- Tool: Nmap
- Service: FTP
- Target IP: 192.168.56.102

Step 1: Host Discovery and Port Scanning

Command:

nmap -sS 192.168.56.102

Purpose: To identify open ports on the target machine.

Step 2: FTP Service Enumeration

Command:

nmap -sC -sV -p 21 192.168.56.102

Purpose:

- "-sC" runs default NSE scripts.
- "-sV" detects service versions.
- "-p 21" scans FTP port 21.

Result:

- FTP service found.
- Version identified as vsftpd 2.3.4.
- Anonymous FTP login was reported as allowed.

Step 3: Manual FTP Verification

Command:

ftp 192.168.56.102

Username:

anonymous

Result: FTP login was successful.

Step 4: Directory Enumeration

Commands used inside FTP:

ls
pwd
ls -la

Result:

- FTP login succeeded.
- Remote FTP directory showed "/".
- No additional files were visible in the captured directory listing.

Exit FTP:

quit

Security Finding

Anonymous FTP login was enabled and successfully verified.

Potential Risk

Anonymous access can allow unauthorized users to access files if the server permissions expose them. In this test, no additional files were visible in the captured listing.

Recommendation

- Disable anonymous FTP if it is not required.
- Restrict file and directory permissions.
- Use secure file-transfer alternatives where possible.
- Regularly review FTP server configuration.

Conclusion

This lab helped me practice port scanning, service/version detection, FTP enumeration, manual verification, and security documentation.

Disclaimer

This assessment was performed in my own controlled lab environment for educational purposes only.
