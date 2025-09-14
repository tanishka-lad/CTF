
---

# 🟠 Bandit Level 5 → Level 6 – Precision File Filtering

### 📌 Level Goal  
> The password for the next level is stored in a file somewhere under the `inhere` directory and has all of the following properties:
- ✅ Human-readable  
- ✅ Exactly **1033 bytes** in size  
- ✅ Not executable

---

## 🛠️ Commands You May Need  
`ls`, `cd`, `cat`, `file`, `du`, `find`

---

## 🔍 My Exploration Process

### ❌ Initial Attempts (Time-Consuming)
I tried using `du` to measure file sizes:
```bash
du -sb
du -b
du -sh */ | sort -h
du -sb */
```
These gave rough size estimates but weren’t precise enough to isolate a file of **exactly 1033 bytes**. Also, `du` reports **directory sizes**, not individual file sizes in bytes.

---

### ✅ Final Working Command
```bash
find . -type f -size 1033c
```

### 🔍 Why This Works:
- `find` → recursively searches for files.
- `-type f` → restricts to regular files.
- `-size 1033c` → filters files that are **exactly 1033 bytes** (`c` = bytes).

---

## 🔎 Terminal Walkthrough

```bash
bandit5@bandit:~/inhere$ find . -type f -size 1033c
./maybehere07/.file2
```

Found a hidden file inside `maybehere07`.

```bash
cd maybehere07
cat ./file2
```

❌ Error: `No such file or directory`  
This happened because the file is **hidden** (starts with a dot).

✅ Correct command:
```bash
cat ./.file2
```

---

## 🔑 Password Found

```text
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```

Use it to log into **Bandit Level 6**:
```bash
ssh bandit6@bandit.labs.overthewire.org -p 2220
```

---

## 🧠 Reflection

This level teaches:
- How to use `find` with byte-level precision.
- The importance of understanding file visibility (`.` prefix = hidden).
- Why `du` isn’t ideal for forensic file filtering.
- How to combine size, type, and permission filters for adversarial file discovery.

---

