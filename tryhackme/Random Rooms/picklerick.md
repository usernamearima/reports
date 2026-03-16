# THM REPORT – PICKLE RICK (BEGINNER ROOM)

---

## Target Information
- Target: Pickle Rick  
- Platform: TryHackMe  
- Operating System: Linux  
- Difficulty: Easy

---

# 1. Reconnaissance
Initial reconnaissance focused on identifying open services on the target system.

A port scan revealed one main accessible service:

- Port 80/tcp – HTTP

The presence of a web service suggested that the primary attack surface would involve web application enumeration.

---

# 2. Enumeration
Enumeration of the web server was performed by manually browsing the website and inspecting its source code.

Key findings included:

- The webpage source code contained a comment revealing a possible username.
- A `robots.txt` file was discovered, which exposed additional sensitive information.
- The website featured a command panel that allowed interaction with the system.

These findings indicated that sensitive information had been unintentionally exposed through the web application.

---

# 3. Initial Access
Initial access to the command panel was achieved using credentials discovered during enumeration.

The login panel accepted the username discovered in the source code along with a password obtained from the `robots.txt` file.

After successful authentication, the command execution interface became accessible.

---

# 4. Command Execution
The command panel allowed execution of system commands on the server.

Although certain commands were restricted, it was possible to bypass these limitations by using alternative commands available in the system.

Directory navigation and file listing commands were used to explore the filesystem.

---

# 5. Flag Discovery
Three ingredient files (flags) were located in different directories on the system.

Typical enumeration steps included:

- Listing directories
- Navigating through system paths
- Reading files containing the ingredients

The flags were retrieved by using file reading commands on the discovered files.

---

# 6. Privilege Level
The command panel executed commands with elevated privileges, effectively granting high-level system access.

This allowed unrestricted access to sensitive directories and files.

---

# 7. Impact
Improperly secured command execution interfaces can allow attackers to:

- Execute arbitrary commands on the server
- Access sensitive system files
- Escalate privileges
- Fully compromise the system

Such vulnerabilities represent a critical security risk in real-world environments.

---

# 8. Key Takeaways
- Never expose command execution panels to unauthenticated or weakly authenticated users.
- Sensitive information should not be stored in comments or public files like `robots.txt`.
- Proper input validation and command restrictions must be implemented.
- Web enumeration is often enough to discover critical vulnerabilities.

---

# SUMMARY
The Pickle Rick room demonstrates common web security mistakes:

- Information disclosure through HTML comments and `robots.txt`
- Weak authentication mechanisms
- Remote command execution via insecure web panels

Flow: Recon → Web Enumeration → Credential Discovery → Command Execution → Flag Retrieval
