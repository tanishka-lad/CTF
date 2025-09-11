
## 🗂️ `ls` – List Directory Contents
- **Purpose**: Shows files and folders in the current directory.
- **Usage**:  
  ```bash
  ls
  ls -l        # long format with permissions, owner, size
  ls -a        # includes hidden files (starting with .)
  ```
- **CTF Tip**: Use `ls -la` to spot hidden files like `.hidden` or `.flag`.

---

## 📁 `cd` – Change Directory
- **Purpose**: Moves you into a different folder.
- **Usage**:  
  ```bash
  cd /home/bandit0
  cd ..        # go up one level
  cd ~         # go to home directory
  ```
- **CTF Tip**: Navigate carefully—some flags are buried deep in nested folders.

---

## 📖 `cat` – Concatenate and Display File
- **Purpose**: Reads and prints the contents of a file.
- **Usage**:  
  ```bash
  cat readme.txt
  cat /etc/passwd
  ```
- **CTF Tip**: Use `cat` to reveal flags, passwords, or hints inside text files.

---

## 🧪 `file` – Identify File Type
- **Purpose**: Tells you what kind of file you're dealing with (text, binary, script, etc.).
- **Usage**:  
  ```bash
  file script.sh
  file suspicious_file
  ```
- **CTF Tip**: Great for spotting disguised files—e.g., a `.jpg` that’s actually a ZIP.

---

## 📦 `du` – Disk Usage
- **Purpose**: Shows how much space files or folders take up.
- **Usage**:  
  ```bash
  du -sh *     # summary in human-readable format
  du -a        # includes files and directories
  ```
- **CTF Tip**: Useful for finding large hidden files or checking where data is stored.

---

## 🔍 `find` – Search for Files
- **Purpose**: Locates files based on name, type, size, permissions, etc.
- **Usage**:  
  ```bash
  find . -name "flag*"
  find / -type f -size +1M
  find . -perm 4000
  ```

---

# 🟢 Bandit Level 0 → Level 1 – Finding the First Password

### 📌 Level Goal
> The password for the next level is stored in a file called `readme` located in the home directory.  
> Use this password to log into `bandit1` using SSH on **port 2220**.

---

## 🛠️ Commands Used

```bash
cd ~          # Navigate to home directory
cd            # Also works to go to home
ls            # List files in the current directory
cat readme    # Display contents of the readme file
```

---

## 🔍 Step-by-Step Breakdown

1. **`cd ~` or `cd`**  
   - Both commands take you to the user's home directory.  
   - `~` is shorthand for the current user's home path (e.g., `/home/bandit0`).

2. **`ls`**  
   - Lists all files in the current directory.  
   - Output showed a file named `readme`.

3. **`cat readme`**  
   - Displays the contents of the `readme` file.  
   - This file contains the password for the next level.

---

## 🔑 Password Found

```text
ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If
```

Use this to log into **bandit1**:
```bash
ssh bandit1@bandit.labs.overthewire.org -p 2220
```

---

## 🧠 Reflection

This level introduces basic Linux navigation and file reading:
- `cd` and `ls` help explore the filesystem.
- `cat` is essential for viewing file contents—especially flags and passwords.
- Understanding the home directory structure is key for progressing through Bandit.

