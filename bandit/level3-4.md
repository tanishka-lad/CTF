
---

# 🟢 Bandit Level 3 → Level 4 – Hidden File Discovery

### 📌 Level Goal
> The password for the next level is stored in a **hidden file** inside the `inhere` directory.

---

## 🛠️ Commands Used
```bash
cd ~
cd inhere
ls
ls -a
find
cat ./...Hiding-From-You
```

---

## 🔍 Step-by-Step Breakdown

1. **Navigate to the target directory**:
   ```bash
   cd ~
   cd inhere
   ```

2. **List visible files**:
   ```bash
   ls
   ```
   ❌ No output—no visible files.

3. **Reveal hidden files**:
   ```bash
   ls -a
   ```
   ✅ Output:
   ```
   .  ..  ...Hiding-From-You
   ```

   - `.` and `..` are standard directory references.
   - `...Hiding-From-You` is a hidden file (starts with a dot).

4. **Confirm file presence with `find`**:
   ```bash
   find
   ```
   ✅ Output:
   ```
   .
   ./...Hiding-From-You
   ```

5. **Read the hidden file**:
   ```bash
   cat ./...Hiding-From-You
   ```
   ✅ Output:
   ```
   2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
   ```

---

## 🔑 Password Found

```text
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

Use it to log into **Bandit Level 4**:
```bash
ssh bandit4@bandit.labs.overthewire.org -p 2220
```

---

## 🧠 Technical Insight

### 🔹 Why `...Hiding-From-You` Is Hidden
- Files starting with a dot (`.`) are hidden by default in Unix/Linux.
- `ls` ignores them unless you use `ls -a`.

### 🔹 Why `cat ./...Hiding-From-You` Works
- The filename starts with `...`, not `-`, so it doesn’t confuse the shell.
- The `./` prefix ensures the shell treats it as a file path, not a command or option.

---

## 🧵 Reflection

This level reinforces:
- The importance of `ls -a` and `find` for uncovering hidden files.
- How shell parsing treats filenames with dots and dashes.
- A subtle lesson in adversarial file naming—perfect for CTFs and forensic analysis.

---

