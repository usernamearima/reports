# THM REPORT – BLUE (BEGINNER ROOM)

---

## Target Information
- Target: Blue  
- Platform: TryHackMe  
- Operating System: Windows  
- Difficulty: Easy

---

# 1. Reconnaissance
Initial reconnaissance involved scanning for open ports and services.

A port scan revealed the following:

- Port 445/tcp – SMB  
- Port 3389/tcp – RDP  
- Port 135/tcp – RPC  

The SMB service was identified as the primary attack surface for initial access.

---

# 2. Enumeration
Enumeration focused on SMB to identify accessible shares.

Key observations:

- Anonymous access to SMB shares was allowed.  
- Listing shares revealed a folder named `Documents` containing a text file.  
- Standard SMB enumeration tools confirmed the presence of readable files without authentication.

This demonstrates a common misconfiguration in Windows environments.

---

# 3. Initial Access
Initial access was obtained via anonymous SMB login:

- Tools like `smbclient` were used to connect without credentials.  
- The shared folder was successfully mounted, allowing file listing and retrieval.  

No exploitation of vulnerabilities was required.

---

# 4. Information Disclosure
The shared `Documents` folder contained:

- `user.txt` – the user flag  
- Additional text files containing hints and credentials  

The files were readable by anyone connecting to the SMB share, leading to direct disclosure.

---

# 5. Privilege Level
Access was limited to an unauthenticated SMB guest user.

Privilege escalation was not required for the scope of this room.

---

# 6. Impact
An attacker could:

- Access sensitive files anonymously  
- Obtain user flags without any authentication  
- Potentially leverage discovered credentials for further access  

This illustrates the risk of misconfigured Windows file sharing.

---

# 7. Key Takeaways
- Anonymous SMB access is a critical misconfiguration.  
- Sensitive files should never be placed in public shares.  
- Enumeration alone can lead to full compromise in beginner-level machines.  
- Always configure proper access controls on Windows services.

---

# SUMMARY
The Blue room on TryHackMe demonstrates:

- Windows SMB misconfigurations leading to information disclosure  
- Basic enumeration as the primary attack vector  
- No exploits or credentials required  

Flow: Recon → SMB Enumeration → Guest Access → Data Exposure → User Flag  
