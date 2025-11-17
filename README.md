# 🔐 Weak Password Security Project

**Course:** BFOR 419 – Cybersecurity Risk Management  
**Student:** Shekeeb Shadab Ghiasi  
**Instructor:** De Oliveira Lima, Vinicius  
**Term:** Fall 2025  

---

## 🌟 Project Overview

Weak and reused passwords remain one of the biggest vulnerabilities in cybersecurity.  
This project demonstrates how attackers exploit insecure passwords and how strong password practices and MFA prevent compromise.

The project uses a virtual lab simulation (**Kali Linux attacker → Ubuntu SSH server**) to test:
- brute-force attacks,
- dictionary attacks,  
- and offline hash cracking.

---

## 🎯 Objectives

- Understand behavioral and technical causes of weak password use  
- Demonstrate Hydra brute-force attacks on SSH  
- Demonstrate offline cracking with John the Ripper  
- Evaluate protection strategies: strong passwords, password managers, MFA  
- Present results with professional documentation  

---
[01_Ubuntu_Server_Installed_on_VM.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/01_Ubuntu_Server_Installed_on_VM.png)
## 🖥️ Lab Setup Overview

### **Virtual Machines**
- **Kali-Attacker** – brute-force testing  
- **Ubuntu-Server** – SSH enabled target  
- **Metasploitable2** (optional for hash testing)

### **Users Created**
- `weakuser` – weak password  
- `stronguser` – strong Bitwarden-generated password  

### **Network**
- VirtualBox **Host-Only Adapter** for safe isolated testing

---

## 📂 Repository Structure


Network	Host-Only Adapter
📂 Repository Structure
``` 
WeakPasswordSecurityProject/
│
├── Lab_Screenshots/
│   ├── [01_Ubuntu_Server_Installed_on_VM.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/01_Ubuntu_Server_Installed_on_VM.png)
│   ├── 01_Ubuntu_Server_Installed_on_VM.png
│   ├── 02_Kali-Attacker_Installed_on_VM.png
│   ├── 03_Network_Config_on_Kali.png
│   ├── 04_Network_Config_on_Ubuntu.png
│   ├── 05_Ubuntu_Server_Get_IP.png
│   ├── 06_Kali_Ping_Ubuntu.png
│   ├── 07_Server_Config_Install_SSH.png
│   ├── 08_Create_Weak_Password.png
│   ├── 09_Attacker_Password_Tool.png
│   ├── 10_Nmap_Scan.png
│   ├── 11_Hydra_Attack_Weak_User.png
│   ├── 12_Create_Strong_User.png
│   ├── 13_Offline_Attack_John.png
│   ├── 14_Export_Hashes.png
│   ├── 15_Copy_Hashes_SCP.png
│   ├── 16_John_Crack.png
│   ├── 17_John_Results.png
│   ├── 18_Bitwarden.png
│   ├── 19_Create_Vault_Entry.png
│   ├── 20_Username_Stronguser.png
│   ├── 21_Password_Generator.png
│   ├── 22_MFA_Demo.png
│   ├── 23_Users_List.png
│
├── Results/
│   └── password_attack_results.xlsx
│
└── Configs/
    └── weak_passwords.txt
```


## 🔥 Attack Scenarios Tested

### **1️⃣ Hydra SSH — Weak Password**
- **User:** `weakuser`  
- **Cracked:** ✅ Yes  
- **Time:** ~5 seconds  
- **Result:** Success  

---

### **2️⃣ Hydra SSH — Strong Password**
- **User:** `stronguser`  
- **Password:** 20+ random Bitwarden password  
- **Cracked:** ❌ No  
- **Time tested:** 2 minutes  
- **Result:** Failed (Strong)  

---

### **3️⃣ John the Ripper — Offline Hash**
- **Hash type:** /etc/shadow extract  
- **Cracked:** ✅ Yes  
- **Time:** ~10 seconds  

---

## 📊 Results Summary

The virtual lab proved that **weak passwords are extremely vulnerable**,  
while **strong, randomly generated passwords resist attacks**.

### **Key Findings**
- Weak SSH password was cracked in **5 seconds**  
- Strong SSH password **did not crack**  
- John the Ripper cracked weak offline password **instantly**  
- MFA blocked login even when the password was known  

---

## 🔒 Conclusion

Using:
- password managers  
- strong passwords  
- MFA  

**dramatically reduces credential compromise risk.**

---

## 📜 License

This project is for academic use only as part of the University at Albany’s  
**BFOR 419 – Cybersecurity Risk Management** course.

---

## ✍️ Prepared By

**Shekeeb Shadab Ghiasi**  
University at Albany – Fall 2025  
