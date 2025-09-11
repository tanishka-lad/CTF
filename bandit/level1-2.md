
---

## 🧩 Level Goal
> The password for the next level is stored in a file called `-` located in the home directory.

---

## 🧠 The Challenge
The filename is literally a **dash (`-`)**, which is tricky because most Linux commands interpret `-` as an **option flag**, not a filename.

So if you run:
```bash
cat -
```
It won’t read the file—it’ll wait for input from your keyboard (stdin), which is not what we want.

---

## ✅ Solution – Step-by-Step

1. **Navigate to the home directory** (if you're not already there):
   ```bash
   cd ~
   ```

2. **List the files** to confirm the presence of `-`:
   ```bash
   ls -l
   ```

3. **Read the file safely using `cat`**:
   ```bash
   cat ./-
   ```

   ✅ Why this works:
   - `./-` tells the shell: “This is a file named `-` in the current directory.”
   - The `./` prefix avoids confusion with command-line options.

---

## 🔑 Password Found

Once you run `cat ./-`, you’ll see the password for **Bandit Level 2**. Use it to log in like this:
```bash
ssh bandit2@bandit.labs.overthewire.org -p 2220
```

---

## 🧠 Bonus: Why This Matters in CTFs

- Filenames like `-`, `--`, or even `..` are used to test your understanding of shell behavior.
- Knowing how to escape or prefix special characters is key in adversarial environments.

---

