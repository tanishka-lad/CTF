

# 🟢 Bandit Level 0 – SSH Login Basics

### 📌 Challenge Description
> The goal of this level is to log into the game using SSH.  
> Host: `bandit.labs.overthewire.org`  
> Port: `2220`  
> Username: `bandit0`  
> Password: `bandit0`  

Once logged in, we can access the Level 1 instructions.

---

## 🛠️ Commands Used
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

---

## 🔍 What We Did – Step-by-Step

1. **Opened the terminal (CMD on Windows)**  
   This is our interface to run shell commands and interact with remote servers.

2. **Used the `ssh` command**  
   SSH (Secure Shell) is a protocol that allows secure remote login from one computer to another. It encrypts the session, protecting data from eavesdropping.

3. **Specified the username and host**  
   - `bandit0@bandit.labs.overthewire.org` tells SSH to log in as user `bandit0` on the server `bandit.labs.overthewire.org`.

4. **Used the `-p` flag to specify the port**  
   - `-p 2220` tells SSH to connect using **port 2220** instead of the default port 22.  
   - This is important because OverTheWire Bandit uses a **non-standard port** to avoid interference or scanning.

5. **Entered the password when prompted**  
   - The password is also `bandit0`. Once entered correctly, we gain access to the Bandit Level 0 shell.

---

## 🧠 What Is Port 2220?

Ports are like doors into a server.  
- **Port 22** is the default for SSH.  
- **Port 2220** is a custom port chosen by OverTheWire to isolate the Bandit game environment.  
- Using a non-standard port helps avoid automated scans and keeps the challenge environment secure.

---

## ✅ Outcome

After logging in:
- We are inside the Bandit Level 0 shell.
- We can now run Linux commands to explore the system.
- The next step is to read the instructions for Level 1, typically found in a file like `readme` in the home directory.

---

## 🧵 Reflection

This level introduces the basics of remote access using SSH—a foundational skill in cybersecurity and CTFs. Understanding how to specify ports and authenticate securely sets the stage for deeper exploration in later levels.


