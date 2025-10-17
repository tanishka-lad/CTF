
---

# 🛡️ OverTheWire Bandit CTF Writeup  
## 🎯 Challenge: Bandit Level 9 → Level 10

### 📌 Level Goal  
> The password for the next level is stored in the file `data.txt` in one of the few **human‑readable strings**, preceded by several `=` characters.

---

## 🧭 Step‑by‑Step Solution

### 1. Inspect the file type
```bash
ls -a
```
- Lists all files in the current directory.  
- Confirms that `data.txt` exists.

```bash
file data.txt
```
- Identifies the file type.  
- In this case, it’s not plain text but contains binary data.

---

### 2. Extract human‑readable strings
```bash
strings data.txt
```
- `strings` scans through the binary file and prints only **printable ASCII text**.  
- This is useful when the file is mostly unreadable but may hide clues or passwords.

---

### 3. Locate the password
- From the `strings` output, look for the line with **several `=` characters**.  
- The password is found immediately after those `=` signs.

---

## 🔧 Commands Explained

| Command   | Purpose |
|-----------|---------|
| `ls -a`   | Lists all files, including hidden ones |
| `file`    | Identifies the type of a file |
| `strings` | Extracts human‑readable text from binary files |

---

## ✅ Summary

- **Challenge solved using:**  
  ```bash
  strings data.txt
  ```
- **Password for Level 10:**  
  ```
  FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
  ```

---

