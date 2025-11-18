# 🖼️ Lab Screenshots Description

A detailed explanation of each screenshot captured during the Weak Password Security Project lab.

---

## 🔧 01 — Ubuntu Server Installed on VM  
### **Ubuntu-Server VM Created**
- Purpose: Target machine (victim server)  
- OS: Ubuntu Server 24.04 LTS  
- Memory: 4096 MB  
- Disk: 20–30 GB  

---

## 🛡️ 02 — Kali Attacker Installed on VM  
### **Kali-Attacker VM Created**
- Purpose: Attacker machine  
- OS: Kali Linux rolling  
- Memory: 4096 MB  
- Disk: 30–40 GB  

---

## 🌐 03 — Network Config on Kali  
## 🌐 04 — Network Config on Ubuntu  
### **Network Configuration (Bridged Mode)**  
For both VMs:  
**Settings → Network → Adapter 1**
- ✔ Enable Network Adapter  
- ✔ Attached to: Bridged Adapter  
- ✔ Device: Your Wi-Fi card (Intel AX201 or similar)  

---

## 🔎 05 — Ubuntu Server: Get IP  
### **Confirm Network Connection**
- `ip a`  
- Ubuntu-Server IP: **192.168.1.174**  

---

## 📶 06 — Kali Ping Ubuntu  
### **Ping Test to Check Connectivity**
Command:  
`ping 192.168.1.174`

If you see:  
`64 bytes from 192.168.1.174: icmp_seq=1 ttl=64 time=…`

Then:  
- ✔ Communication works  
- ✔ Lab network successful  
- ✔ VMs are on the same network  

---

## 🔐 07 — Install SSH on Ubuntu Server  
### **Server Configuration – Install SSH**
Commands:
- `sudo apt update`  
- `sudo apt install openssh-server -y`  
- `sudo systemctl enable ssh`  
- `sudo systemctl start ssh`  
- `sudo systemctl status ssh` → **active (running)**  

---

## 🧪 08 — Create Weak Password User  
### **Weak User Creation**
Command:  
`sudo adduser weakuser`

- Password: **Ann123** (intentionally weak)  
- Name: Shekeeb  
- Room Number: 123  
- Work Phone: 444444444  

---

## 🧪 09 — Create Strong Password User  
### **Strong User Creation**
Command:  
`sudo adduser stronger`  
Password: **MyS3cureP@ss2025**

Fields:  
- Name: Ghiasi  
- Room Number: 123  
- Work Phone: 44444  

---

## 🛰️ 10 — Nmap Scan  
### **Attack & Password Cracking — Tool Setup & Nmap Scan**

Install tools:
- `sudo apt update`  
- `sudo apt install nmap hydra medusa john wordlists -y`

Scan Ubuntu server:  
`nmap -sV 192.168.1.174`

Expected:
- Port 22 open  
- SSH detected  
- Service: OpenSSH  

---

## 💥 11 — Hydra Attack (Weak User)  
### **Password Attack Using Hydra**
Command:  
`hydra -l weakuser -p Ann123 ssh://192.168.1.174`

Expected:
- ✔ Login found  
- ✔ Password cracked instantly  
- Time to crack: **< 1 second**  

---

## 🔐 12 — Hydra Test on Strong User  
### **Your Explanation (kept EXACTLY):**

For the strong account (stronger with password MyS3cureP@ss2025), I tested Hydra using a single known candidate password.  
Hydra reported a successful login because I supplied the correct password directly with the -p option.  
In a realistic attack, a brute-force or dictionary attack would be extremely unlikely to guess this long, complex password,  
especially if account lockout and rate limiting were enabled. This demonstrates that strong,
unique passwords are resistant to automated guessing, and Hydra only succeeded here because the exact password was already known.

For the weak user (weakuser), Hydra would be able to crack the password even without knowing it ahead of time,  
because weak passwords are short and appear in common wordlists.  
For the strong user (stronger), Hydra only succeeded because I manually supplied the exact password using the -p option.  
In a real attack scenario, this strong password (MyS3cureP@ss2025!) would not be cracked by brute-force or dictionary attacks,  
demonstrating the importance of strong password policies.

---

## 🧩 13 — Offline Attack with John  
Install John:  
`sudo apt install john -y`  

---

## 📤 14 — Export Password Hashes  
Command:  
`sudo unshadow /etc/passwd /etc/shadow | sudo tee /tmp/passwords.txt`  

---

## 🔁 15 — Copy Hashes to Kali (SCP)  
On Kali:
- `mkdir -p ~/hashes`  
- `cd ~/hashes`  
- `scp serveradmin@192.168.1.174:/tmp/passwords.txt .`

(Change serveradmin & IP if needed.)  
It will ask for your Ubuntu password.

---

## 🔓 16 — Crack Hashes with John  
Start cracking:  
- `john passwords.txt`  
Show results:  
- `john --show passwords.txt`  

---

## 📊 17 — John Results  
- Weakuser: **NOT cracked**  
- Stronguser: **NOT cracked**  

### **Your Explanation (kept EXACTLY):**

Although the user weakuser was assigned the password “Ann123”, this password is not truly weak in a cybersecurity context.  
It mixes a name with small numbers and capital letter, making it less likely to appear in common dictionary wordlists.  

Cybersecurity “weak passwords” are things like:  
- 12345  
- password / password1  
- admin / admin123  

---

## 🔑 18–21 — Password Manager Screenshots  
### **Password Manager (Bitwarden or KeePassXC)**  
Example: Bitwarden  
1. Install Bitwarden  
2. Create vault entry:  
- Username: `stronguser`  
- Password: generated 20+ character random password (with symbols)

This demonstrates how password managers make it practical to use **very strong, unique passwords** resistant to brute-force or wordlist attacks.

---

## 📱 22 — MFA Demo  
### **Using UAlbany MFA (sghiasi@albany.edu)**  

---

## 👥 23 — Users List  
List of created users on Ubuntu Server.  

---

## 📂 Supporting Files  
- **Results/password_attack_results.xlsx** → Summary of attack results  
- **Configs/weak_passwords.txt** → Weak password wordlist used  
