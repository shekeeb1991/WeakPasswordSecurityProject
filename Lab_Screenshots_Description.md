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

## 🛡️ [02_Kali-Attacker_Installed_on_VM.png](Lab_Screenshots/02_Kali-Attacker_Installed_on_VM.png)
### **Kali-Attacker VM Created**
- Purpose: Attacker machine
- OS: Kali Linux rolling
- Memory: 4096 MB
- Disk: 30–40 GB

---

## 🌐 [03_Network_Config_on_Kali.png](Lab_Screenshots/03_Network_Config_on_Kali.png)  
## 🌐 [04_Network_Config_on_Ubuntu.png](Lab_Screenshots/04_Network_Config_on_Ubuntu.png)
### **Network Configuration (Bridged Mode)**
For both VMs:  
Settings → Network → Adapter 1
- ✔ Enable Network Adapter
- ✔ Attached to: Bridged Adapter
- ✔ Device: Your Wi-Fi card (Intel AX201 or similar)

---

## 🔎 [05_Ubuntu_Server_Get_IP.png](Lab_Screenshots/05_Ubuntu_Server_Get_IP.png)
### **Confirm Network Connection**
- `ip a`
- Ubuntu-Server IP: **192.168.1.174**

---

## 📶 [06_Kali_Ping_Ubuntu.png](Lab_Screenshots/06_Kali_Ping_Ubuntu.png)
### **Kali: Ping Ubuntu**
Command:  
`ping 192.168.1.174`

If you see:  
`64 bytes from 192.168.1.174: icmp_seq=1 ttl=64 time=…`
- ✔ Communication works
- ✔ Lab environment successful
- ✔ VMs are on the same network

---

## 🔐 [07_Server_Config_Install_SSH.png](Lab_Screenshots/07_Server_Config_Install_SSH.png)
### **Server Configuration – Install SSH**
Commands:
- `sudo apt update`
- `sudo apt install openssh-server -y`
- `sudo systemctl enable ssh`
- `sudo systemctl start ssh`
- `sudo systemctl status ssh` → **active (running)**

---

## 🧪 [08_Create_Weak_Password.png](Lab_Screenshots/08_Create_Weak_Password.png)
### **Create a Weak Password User**
Command:  
`sudo adduser weakuser`

- Password: **Ann123**  
- Name: Shekeeb
- Room Number: 123
- Work Phone: 444444444

---

## 🧪 [09_Attacker_Password_Tool.png](Lab_Screenshots/09_Attacker_Password_Tool.png)
### **Create a Strong Password User**
Command:  
`sudo adduser stronger`  
Password: **MyS3cureP@ss2025**

Fields:
- Name: Ghiasi
- Room Number: 123
- Work Phone: 44444

---

## 🛰️ [10_Nmap_Scan.png](Lab_Screenshots/10_Nmap_Scan.png)
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

## 💥 [11_Hydra_Attack_Weak_User.png](Lab_Screenshots/11_Hydra_Attack_Weak_User.png)
### **Password Attack Using Hydra**
Command:  
`hydra -l weakuser -p Ann123 ssh://192.168.1.174`

Expected:
- ✔ Login found
- ✔ Password cracked instantly
- Time to crack: **< 1 second**

---

## 🔐 [12_Create_Strong_User.png](Lab_Screenshots/12_Create_Strong_User.png)
### **Hydra Test on Strong User**

**Your Explanation (kept EXACTLY):**  
For the strong account (stronger with password MyS3cureP@ss2025), I tested Hydra using a single known candidate password.  
Hydra reported a successful login because I supplied the correct password directly with the -p option.  
In a realistic attack, a brute-force or dictionary attack would be extremely unlikely to guess this long, complex password.

For weakuser: weak passwords appear in wordlists.  
For stronger: Hydra only succeeded because the password was manually provided.

---

## 🧩 [13_Offline_Attack_John.png](Lab_Screenshots/13_Offline_Attack_John.png)
### **Offline Attack with John the Ripper**
Install John:  
`sudo apt install john -y`

---

## 📤 [14_Export_Hashes.png](Lab_Screenshots/14_Export_Hashes.png)
### **Export password hashes**
Run:
`sudo unshadow /etc/passwd /etc/shadow | sudo tee /tmp/passwords.txt`

---

## 🔁 [15_Copy_Hashes_SCP.png](Lab_Screenshots/15_Copy_Hashes_SCP.png)
### **Copy hashes to Kali using SCP**
On Kali:
- `mkdir -p ~/hashes`
- `cd ~/hashes`
- `scp serveradmin@192.168.1.174:/tmp/passwords.txt .`

---

## 🔓 [16_John_Crack.png](Lab_Screenshots/16_John_Crack.png)
### **Crack hashes with John**
- `john passwords.txt`
- `john --show passwords.txt`

---

## 📊 [17_John_Results.png](Lab_Screenshots/17_John_Results.png)
### **John Results**
- Weakuser: NOT cracked  
- Stronguser: NOT cracked  

**Your Explanation (kept EXACTLY):**  
Ann123 is not extremely weak — it does not appear in common wordlists like:  
- 12345  
- password1  
- admin123  

---

## 🔑 [18_Bitwarden.png](Lab_Screenshots/18_Bitwarden.png)  
## 🔑 [19_Create_Vault_Entry.png](Lab_Screenshots/19_Create_Vault_Entry.png)  
## 🔑 [20_Username_Stronguser.png](Lab_Screenshots/20_Username_Stronguser.png)  
## 🔑 [21_Password_Generator.png](Lab_Screenshots/21_Password_Generator.png)
### **Password Manager Demonstration**
- Create secure passwords  
- Store credentials safely  

---

## 📱 [22_MFA_Demo.png](Lab_Screenshots/22_MFA_Demo.png)
### **MFA Demo Using UAlbany Account**

---

## 👥 [23_Users_List.png](Lab_Screenshots/23_Users_List.png)
List of created users on Ubuntu Server.

---

## 📂 Supporting Files  
- **[password_attack_results.xlsx](Results/password_attack_results.xlsx)**  
- **[weak_passwords.txt](Configs/weak_passwords.txt)**  
