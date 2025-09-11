
---

# 🟡 Bandit Level 1 → Level 2 – Handling Special Filenames

### 📌 Level Goal
> The password for the next level is stored in a file called `-` located in the home directory.

---

## 🛠️ Commands Used

```bash
cd ~          # Navigate to home directory
ls -l         # List files with details
cat ./-       # Read the file named "-"
```

---

## 🔍 Step-by-Step Breakdown

1. **`cd ~`**  
   - Moves to the user's home directory (`/home/bandit1`).

2. **`ls -l`**  
   - Lists all files with metadata.  
   - Confirms the presence of a file literally named `-`.

3. **`cat ./-`**  
   - Reads the contents of the file named `-`.  
   - The `./` prefix tells the shell to treat `-` as a filename, not a command-line option.

---

## ⚠️ Why `cat -` Doesn’t Work

- `cat -` reads from **standard input**, not the file named `-`.
- Without `./`, the shell misinterprets the filename as an option.

---

## 🔑 Password Found

```text
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

Use this to log into **Bandit Level 2**:
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

---

## 🧠 Reflection

This level teaches:
- How special characters in filenames can affect command behavior.
- The importance of **prefixing with `./`** to disambiguate filenames from options.
- A subtle but powerful lesson in shell parsing—critical for adversarial analysis and CTFs.

---
