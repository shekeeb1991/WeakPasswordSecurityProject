#### Lab Screenshots Description

---

### **01_Ubuntu_Server_Installed_on_VM.png**
**Ubuntu-Server VM Created**
- Purpose: Target machine (victim server)
- OS: Ubuntu Server 24.04 LTS
- Memory: 4096 MB
- Disk: 20–30 GB

---

### **02_Kali-Attacker_Installed_on_VM.png**
**Kali-Attacker VM Created**
- Purpose: Attacker machine
- OS: Kali Linux rolling
- Memory: 4096 MB
- Disk: 30–40 GB

---

### **03_Network_Config_on_Kali.png**
### **04_Network_Config_on_Ubuntu.png**
**Network Configuration (Bridged Mode)**
Settings → Network → Adapter 1  
- ✔ Enable Network Adapter  
- ✔ Attached to: Bridged Adapter  
- ✔ Name: Wi-Fi card (Intel AX201 or similar)

---

### **05_Ubuntu_Server_Get_IP.png**
**Confirm Network Connection**
- Command: `ip a`
- Ubuntu Server IP: **192.168.1.174**

---

### **06_Kali_Ping_Ubuntu.png**
**Kali to Ubuntu Connectivity Test**
Command:
`ping 192.168.1.174`

If you see:
`64 bytes from 192.168.1.174…`
- ✔ Communication works  
- ✔ Lab setup correct  
- ✔ Same network confirmed  

---

### **07_Server_Config_Install_SSH.png**
**Install & Enable SSH on Ubuntu**
- `sudo apt update`
- `sudo apt install openssh-server -y`
- `sudo systemctl enable ssh`
- `sudo systemctl start ssh`
- `sudo systemctl status ssh` → **active (running)**

---

### **08_Create_Weak_Password.png**
**Create Weak User**
- `sudo adduser weakuser`
- Password: **Ann123**

User fields (example):
- Name: Shekeeb
- Room: 123
- Work Phone: 444444444

---

### **09_Attacker_Password_Tool.png**
**Create Strong User**
- `sudo adduser stronger`
- Password: **MyS3cureP@ss2025**

Fields:
- Name: Ghiasi  
- Room: 123  
- Phone: 44444  

---

### **10_Nmap_Scan.png**
**Nmap Scan from Kali**
Install tools:
- `sudo apt update`
- `sudo apt install nmap hydra medusa john wordlists -y`

Scan:
`nmap -sV 192.168.1.174`

Expected:
- Port 22 open  
- OpenSSH detected  

---

### **11_Hydra_Attack_Weak_User.png**
**Hydra Attack — Weak User**
- `hydra -l weakuser -p Ann123 ssh://192.168.1.174`

Expected:
- ✔ Login found  
- ✔ Password cracked  
- Time: **<1 second**

---

### **12_Create_Strong_User.png**
**Hydra Test — Strong User**
Your explanation (kept exactly):

> Hydra succeeded only because the **correct password was supplied** with `-p`.  
> In a real attack, brute-force/dictionary would **not** guess this strong password.  
> Shows importance of strong unique passwords.

---

### **13_Offline_Attack_John.png**
Install John:
`sudo apt install john -y`

---

### **14_Export_Hashes.png**
Export:
`sudo unshadow /etc/passwd /etc/shadow | sudo tee /tmp/passwords.txt`

---

### **15_Copy_Hashes_SCP.png**
Copy hashes to Kali:
