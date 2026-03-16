# HTB REPORT – REDEEMER (BEGINNER LAB)

---

## Target Information
- Target: Redeemer
- Platform: Hack The Box
- Operating System: Linux
- Difficulty: Very Easy

---

# 1. Reconnaissance
A network scan was performed to identify active services on the target.

The scan revealed the following open port:

- Port 6379/tcp – Redis

Redis is an in-memory database that should not be exposed without authentication.

---

# 2. Enumeration
Enumeration of the Redis service was performed using the Redis command-line interface.

The service did not require authentication, allowing full interaction with the database.

This indicates an insecure Redis configuration.

---

# 3. Initial Access
Initial access was obtained by connecting directly to the Redis service:

redis-cli -h <target_ip>

The connection was established successfully without credentials.

---

# 4. Information Disclosure
By enumerating the Redis keyspace, a key containing the user flag was discovered.

The value of the key was retrieved directly from the database, exposing sensitive information.

---

# 5. Privilege Level
Access is limited to interaction with the Redis service.

No shell access or privilege escalation is required as per the design of the machine.

---

# 6. Impact
An unauthenticated attacker can read data stored in the Redis database.

This may include sensitive application data, session tokens, or credentials in real-world scenarios.

---

# 7. Key Takeaway
- Redis should never be exposed without authentication
- Misconfigured databases lead to immediate data leaks
- Service enumeration is critical during reconnaissance
- Databases are high-value targets

---

# SUMMARY
The REDEEMER machine highlights risks related to database exposure:

- Unprotected services allow direct data access
- No exploitation is needed when misconfigurations exist
- Understanding common services is essential for beginners

Flow: Recon → Redis Enumeration → Unauthenticated Access → Data Disclosure
