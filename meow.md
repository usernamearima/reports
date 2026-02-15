# HTB REPORT – MEOW (BEGINNER LAB)

TARGET: MEOW
PLATFORM: Hack The Box
OS: Linux
DIFFICULTY: Very Easy
================================

1. Reconnaissance
Wykonano podstawowy skan portów. Zidentyfikowano otwartą usługę Telnet (port 23). Brak innych istotnych usług sieciowych.

2. Enumeration
Usługa Telnet była dostępna bez odpowiednich zabezpieczeń. Brak mechanizmu uwierzytelniania lub możliwość logowania bez hasła.

3. Initial Access
Uzyskano bezpośredni dostęp do systemu poprzez połączenie Telnet bez konieczności podawania danych logowania.

4. Privilege Level
Dostęp został uzyskany bezpośrednio na poziomie root, bez potrzeby eskalacji uprawnień.

5. Impact
Pełna kompromitacja systemu. Atakujący uzyskuje całkowitą kontrolę nad maszyną bez użycia exploitów, wyłącznie poprzez brak zabezpieczeń usługi zdalnego dostępu.

6. Key Takeaway
Niezabezpieczony Telnet stanowi krytyczne zagrożenie. Usługi zdalnego dostępu muszą być chronione uwierzytelnianiem lub całkowicie wyłączone.

SUMMARY
================================

MEOW pokazuje absolutne podstawy bezpieczeństwa:
– brak uwierzytelniania = natychmiastowy dostęp
– nie każdy atak wymaga exploita
– błędna konfiguracja jest często najgroźniejszą podatnością

Flow: Recon → Telnet → Brak auth → Root access.
