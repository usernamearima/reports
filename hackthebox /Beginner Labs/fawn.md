HTB REPORT – FAWN (BEGINNER LAB)

================================
TARGET: FAWN
PLATFORM: Hack The Box
OS: Linux
DIFFICULTY: Very Easy
================================

1. Reconnaissance
Wykonano podstawowy skan portów. Zidentyfikowano otwartą usługę FTP (port 21). Brak innych istotnych usług sieciowych.

2. Enumeration
Podczas enumeracji usługi FTP wykryto, że serwer umożliwia logowanie anonimowe (anonymous login). Jest to klasyczna błędna konfiguracja.

3. Initial Access
Zalogowano się do usługi FTP jako użytkownik anonymous, bez konieczności podawania hasła. Uzyskano dostęp do plików znajdujących się na serwerze.

4. Information Disclosure
W katalogu FTP odnaleziono plik zawierający flagę użytkownika (user flag). Brak dodatkowych zabezpieczeń dostępu do danych.

5. Privilege Level
W tym labie dostęp ogranicza się do poziomu użytkownika FTP. Brak eskalacji uprawnień do roota (zgodnie z założeniem boxa).

6. Impact
Nieautoryzowany użytkownik może uzyskać dostęp do plików serwera poprzez anonimowy FTP, co prowadzi do ujawnienia wrażliwych danych.

7. Key Takeaway
Anonimowy FTP jest poważnym błędem konfiguracyjnym. Nawet bez exploitów możliwy jest wyciek danych. Enumeracja usług jest kluczowa na samym początku pentestu.

================================
SUMMARY
================================

FAWN uczy podstaw enumeracji usług i pokazuje, że:
– brak uwierzytelniania = dostęp do danych
– nie każdy atak kończy się shellem
– wyciek informacji to też realna podatność

Flow: Recon → Enumeracja FTP → Anonymous Login → Data Exposure.

================================
END OF REPORT
================================
