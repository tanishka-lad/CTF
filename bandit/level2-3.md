
---

# 🟣 Bandit Level 2 → Level 3 – Escaping the Dash Trap

### 📌 Level Goal
> The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory.

---

## 🛠️ Commands You May Need
- `ls`, `cd`, `cat`, `file`, `du`, `find`

---

## 🔍 Step-by-Step Exploration

1. **Navigated to the home directory**:
   ```bash
   cd ~
   ```

2. **Listed files to confirm the target**:
   ```bash
   ls -l
   ```
   ✅ Output showed a file named `--spaces in this filename--`

---

## ❌ What I Tried (and Why It Failed)

### 1. Using quotes:
```bash
cat "--spaces in this filename--"
```
**Why it failed**:  
Even though the filename was quoted, the shell still interpreted `--spaces` as a **command-line option**, not a filename. Many Unix tools treat `--` as a special flag that marks the end of options, so this confused `cat`.

---

### 2. Escaping spaces and dashes:
```bash
cat \-\-spaces\ in\ this\ filename\-\-
```
**Why it failed**:  
While escaping spaces is correct, the leading `--` still triggered the option parser. The shell didn’t treat it as a literal filename.

---

## ✅ What Worked (and Why)

### The winning command:
```bash
cat ./--spaces\ in\ this\ filename--
```

**Why this works**:
- `./` explicitly tells the shell: “This is a file in the current directory.”
- It **disarms the option parser**, so `cat` treats the entire string as a filename—even if it starts with `--`.
- Escaping the spaces ensures the shell doesn’t split the filename into separate arguments.

---

## 🧠 Why `--` Causes Problems

In Unix/Linux:
- `--` is a **special flag** used to signal the **end of command options**.
- For example:  
  ```bash
  rm -- -filename
  ```
  This tells `rm` to treat `-filename` as a file, not an option.

So when a filename starts with `--`, many commands get confused unless you explicitly tell them it’s a file—using `./` or `--` handling tricks.

---

## 🔑 Password Found

```text
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

Use it to log into **Bandit Level 3**:
```bash
ssh bandit3@bandit.labs.overthewire.org -p 2220
```

---

## 🧵 Reflection

This level teaches:
- How filenames can exploit shell parsing behavior.
- The importance of **prefixing with `./`** to avoid option misinterpretation.
- A subtle but powerful lesson in adversarial file naming—perfect for CTFs and real-world pentesting.

---
