🛡️ Weak Password Security Project

Course: BFOR 419 – Cybersecurity Risk Management
Student: Shekeeb Shadab Ghiasi
Instructor: De Oliveira Lima, Vinicius
Term: Fall 2025

📌 Project Overview

Weak and reused passwords remain one of the biggest vulnerabilities in cybersecurity.
This project demonstrates how attackers exploit insecure passwords and how strong
password practices and MFA prevent compromise.

The project uses a virtual lab simulation (Kali Linux attacker → Ubuntu SSH server)
to test brute-force, dictionary, and offline hash cracking attacks.

🎯 Objectives

Understand behavioral and technical causes of weak password use

Demonstrate Hydra brute-force attacks on SSH

Demonstrate offline cracking with John the Ripper

Evaluate protection strategies: strong passwords, password managers, MFA

Present results with professional documentation

🧪 Lab Environment
Component	Description
Attacker VM	Kali Linux (Hydra, John the Ripper)
Target VM	Ubuntu SSH Server
Wordlist	Custom weak_passwords.txt
Password Manager	Bitwarden
MFA Demo	Duo Mobile
Network	Host-Only Adapter
📂 Repository Structure
WeakPasswordSecurityProject/
│
├── Lab_Screenshots/
│   ├── 01_Ubuntu Server Installed on VM.png
│   ├── 02_Kali-Attaker Installed on VM.png
│   ├── 03_Network Config on Kali-Attaker.png
│   ├── 04_Network Config on Ubuntu.png
│   ├── 05_Ubuntu-Server Get IP.png
│   ├── 06_Kali- Ping Ubuntu.png
│   ├── 07_Server Config - Install SSH (Ubuntu-Server).png
│   ├── 08_Creat Weak Password-Ann123.png
│   ├── 09_Attaker Password Install tool.png
│   ├── 10_Scan the Ubunto Server (Nmap).png
│   ├── 11_Password Attack Uisng Hydra (Weak User).png
│   ├── 12_Create Strong Password User-MyS3cureP@ss2025.png
│   ├── 13_Offline Attack with John the Ripper.png
│   ├── 14_Export hashes.png
│   ├── 15_Copy hashes to Kali using SCP.png
│   ├── 16_Crack the hashes with John on Kali.png
│   ├── 17_John results
│   ├── 18_Password Manager (Bitwarden or KeePassXC).png
│   ├── 19_Create a Vlaut Entry.png
│   ├── 20_Username Stronguser.png
│   ├── 21_Bitwarden password generator.png
│   ├── 22_MFA Demo Using UAlbany Account (sghiasi@albany.edu).png
│   ├── 23_Users.png
│   ├── 144_Export hashes.png
│
├── Results/
│   └── password_attack_results.xlsx
│
└── Configs/
    └── weak_passwords.txt

🧵 Attack Scenarios Tested
✔️ 1. Hydra SSH – Weak Password

User: weakuser

Password cracked in 5 seconds

Attack success: Yes

✔️ 2. Hydra SSH – Strong Password

User: stronguser

Password: 20+ random Bitwarden password

Attack ran for 2+ minutes with 0 valid logins

Attack success: ❌ Failed (Strong)

✔️ 3. John the Ripper — Offline Hash

Cracked weak hash in ~10 seconds

📊 Results Summary

The virtual lab proved that weak passwords are extremely vulnerable,
while strong, randomly generated passwords resist attacks.

Key Findings

Weak SSH password was cracked in 5 seconds

Strong SSH password did not crack during testing

John the Ripper cracked weak offline password instantly

MFA (Duo Mobile) blocked login even if password is known

Conclusion

Using password managers, strong passwords, and MFA
dramatically reduces credential compromise risk.

📘 License

This project is for academic use only as part of the University at Albany's
BFOR 419 – Cybersecurity Risk Management course.

👨‍🎓 Prepared By

Shekeeb Shadab Ghiasi
University at Albany — Fall 2025
