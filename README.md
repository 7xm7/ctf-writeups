# 🥒 TryHackMe - Pickle Rick CTF Walkthrough

This is a simple write-up for the Pickle Rick room on TryHackMe. The goal is to find three flags in a vulnerable web server and understand basic CTF enumeration and exploitation techniques.

---

## 🧠 Objectives

- Enumerate the target machine  
- Exploit the web application  
- Gain access to the system  
- Retrieve all 3 flags

---

## 🔍 Reconnaissance

Performed an initial scan with:

    nmap -sV -p- <target-ip>

    Discovered open port: 80/tcp - Apache httpd 2.4.41

    Accessing the website showed a basic Rick & Morty themed page with the message: Rick is sup4r cool

🕵️ Directory Bruteforce

    Used Gobuster to find hidden paths:

    gobuster dir -u http://<target-ip> -w /usr/share/wordlists/dirb/common.txt

Found:

    /robots.txt → contains the string: Wubbalubbadubdub

    /login.php

    /clue.txt → revealed the username: R1ckRul3s

🔐 Login Panel

    Used the credentials:

    Username: R1ckRul3s
    Password: Wubbalubbadubdub

Login successful.
💻 Command Execution

The post-login interface accepts system commands. I used it as a pseudo shell.

Example:

    ls
    cat 

🔑 Flags:

      First Flag: cat /home/rick/first_flag.txt

      Second Flag: cat /var/www/html/assets/second_flag.txt

      Third Flag: cat /root/third_flag.txt

🧪 Lessons Learned:

    - Importance of brute-forcing directories

    - Basic command injection

    - Manual file enumeration

    - Simple privilege escalation


### Contact

Feel free to connect with me or share feedback:

📧 xaviermota7@gmail.com
🔗 [LinkedIn](https://www.linkedin.com/in/xaviermota7/)
