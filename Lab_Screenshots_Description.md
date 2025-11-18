# 🖼️ Lab Screenshots Description

A detailed explanation of each screenshot captured during the Weak Password Security Project lab.

---

## 🔧 [01_Ubuntu Server Installed on VM.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/01_Ubuntu%20Server%20Installed%20on%20VM.png.png)
### **Ubuntu-Server VM Created**
- Purpose: Target machine (victim server)
- OS: Ubuntu Server 24.04 LTS
- Memory: 4096 MB
- Disk: 20–30 GB

---

## 🛡️ [02_Kali-Attacker Installed on VM.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/02_Kali-Attacker%20Installed%20on%20VM.png.png)
### **Kali-Attacker VM Created**
- Purpose: Attacker machine
- OS: Kali Linux rolling
- Memory: 4096 MB
- Disk: 30–40 GB

---

## 🌐 [03_Network Config on Kali-Attaker.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/03_Network%20Config%20on%20Kali-Attaker.png.png)  
## 🌐 [04_Network Config on Ubuntu.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/04_Network%20Config%20on%20Ubuntu.png.png)
### **Network Configuration (Bridged Mode)**
For both VMs:  
Settings → Network → Adapter 1
- ✔ Enable Network Adapter
- ✔ Attached to: Bridged Adapter
- ✔ Device: Your Wi-Fi card (Intel AX201 or similar)

---

## 🔎 [05_Ubuntu-Server Get IP.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/05_Ubuntu-Server%20Get%20IP.png.png)
### **Confirm Network Connection**
- `ip a`
- Ubuntu-Server IP: **192.168.1.174**

---

## 📶 [06_Kali- Ping Ubuntu.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/06_Kali-%20Ping%20Ubuntu.png.png)
### **Kali: Ping Ubuntu**
Command:  
`ping 192.168.1.174`

If you see:  
`64 bytes from 192.168.1.174: icmp_seq=1 ttl=64 time=…`
- ✔ Communication works
- ✔ Lab environment successful
- ✔ VMs are on the same network

---

## 🔐 [07_Server Config - Install SSH (Ubuntu-Server).png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/07_Server%20Config%20-%20Install%20SSH%20(Ubuntu-Server).png.png)
### **Server Configuration – Install SSH**
Commands:
- `sudo apt update`
- `sudo apt install openssh-server -y`
- `sudo systemctl enable ssh`
- `sudo systemctl start ssh`
- `sudo systemctl status ssh` → **active (running)**

---

## 🧪 [08_Creat Weak Password-Ann123.png.png](WeakPasswordSecurityProject/Lab_Screenshots/08_Creat%20Weak%20Password-Ann123.png.png)

### **Create a Weak Password User**
Command:  
`sudo adduser weakuser`

- Password: **Ann123**  
- Name: Shekeeb
- Room Number: 123
- Work Phone: 444444444

---

## 🧪 [09_Attacker Password Install tool.png.png](Lab_Screenshots/09_Attacker%20Password%20Install%20tool.png.png)
### **Create a Strong Password User**
Command:  
`sudo adduser stronger`  
Password: **MyS3cureP@ss2025**

Fields:
- Name: Ghiasi
- Room Number: 123
- Work Phone: 44444

---

## 🛰️ [10_Scan the Ubunto Server (Nmap).png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/10_Scan%20the%20Ubunto%20Server%20(Nmap).png.png)
### **Attack & Password Cracking — Tool Setup & Nmap Scan**

Install tools:
- `sudo apt update`
- `sudo apt install nmap hydra medusa john wordlists -y`

Scan:  
`nmap -sV 192.168.1.174`

Expected:
- Port 22 open
- SSH detected
- Service: OpenSSH

---

## 💥 [11_Password Attack Using Hydra (Weak User)](Lab_Screenshots/11_Password%20Attack%20Using%20Hydra%20(Weak%20User).png.png)
### **Password Attack Using Hydra**
Command:  
`hydra -l weakuser -p Ann123 ssh://192.168.1.174`

Expected:
- ✔ Login found
- ✔ Password cracked instantly
- Time to crack: **< 1 second**

---

## 🔐 [12_Create Strong Password User-MyS3cureP@ss2025.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/12_Create%20Strong%20Password%20User-MyS3cureP@ss2025.png.png)
### **Hydra Test on Strong User**

**Your Explanation (kept EXACTLY):**  
For the strong account (stronger with password MyS3cureP@ss2025), I tested Hydra using a single known candidate password.  
Hydra reported a successful login because I supplied the correct password directly with the -p option.  
In a realistic attack, a brute-force or dictionary attack would be extremely unlikely to guess this long, complex password.

For weakuser: weak passwords appear in wordlists.  
For stronger: Hydra only succeeded because the password was manually provided.

---

## 🧩 [13_Offline Attack with John the Ripper.png.png](https://github.com/shekeeb1991/WeakPasswordSecurityProject/blob/main/WeakPasswordSecurityProject/Lab_Screenshots/13_Offline%20Attack%20with%20John%20the%20Ripper.png.png)
### **Offline Attack with John the Ripper**
Install John:  
`sudo apt install john -y`

---

## 📤 [14a_Export hashes](Lab_Screenshots/144_Export%20hashes.png.png)
[14b_Export hashes](Lab_Screenshots/14_Export%20hashes.png.png)

### **Export password hashes**
Run:
`sudo unshadow /etc/passwd /etc/shadow | sudo tee /tmp/passwords.txt`

---

## 🔁 [15_Copy hashes to Kali using SCP](Lab_Screenshots/15_Copy%20hashes%20to%20Kali%20using%20SCP.png.png)
### **Copy hashes to Kali using SCP**
On Kali:
- `mkdir -p ~/hashes`
- `cd ~/hashes`
- `scp serveradmin@192.168.1.174:/tmp/passwords.txt .`

---

## 🔓 [16_Crack the hashes with John on Kali](Lab_Screenshots/16_Crack%20the%20hashes%20with%20John%20on%20Kali.png.png)
### **Crack hashes with John**
- `john passwords.txt`
- `john --show passwords.txt`

---

## 📊 [17_John results](Lab_Screenshots/17_John%20results.png.png)
### **John Results**
- Weakuser: NOT cracked  
- Stronguser: NOT cracked  

**Your Explanation (kept EXACTLY):**  
Ann123 is not extremely weak — it does not appear in common wordlists like:  
- 12345  
- password1  
- admin123  

---

## 🔑 [18_Password Manager (Bitwarden or KeePassXC)](Lab_Screenshots/18_Password%20Manager%20(Bitwarden%20or%20KeePassXC).png.png)  
## 🔑 [19_Create a Vault Entry](Lab_Screenshots/19_Create%20a%20Vault%20Entry.png.png)  
## 🔑 [20_Username Stronguser](Lab_Screenshots/20_Username%20Stronguser.png.png)  
## 🔑 [21_Bitwarden password generator](Lab_Screenshots/21_Bitwarden%20password%20generator.png.png)
### **Password Manager Demonstration**
- Create secure passwords  
- Store credentials safely  

---

## 📱 [22_MFA Demo Using UAlbany Account](Lab_Screenshots/22_MFA%20Demo%20Using%20UAlbany%20Account%20(sghiasi%40albany.edu).png.png)
### **MFA Demo Using UAlbany Account**

---

## 👥 [23_Users](Lab_Screenshots/23_Users.png.png)
List of created users on Ubuntu Server.

---

## 📂 Supporting Files  
- **[password_attack_results.xlsx](Results/password_attack_results.xlsx)**  
- **[weak_passwords.txt](Configs/weak_passwords.txt)**  
