
---

# 🛡️ OverTheWire Bandit CTF Writeup  
## 🎯 Challenge: Bandit Level 7 → Level 8

### 📌 Level Goal  
> The password for the next level is stored in the file `data.txt`, **next to the word `millionth`**.

---

## 🧭 Step-by-Step Solution

### 1. 🔍 List all files in the directory
```bash
ls -a
```
- `ls`: Lists files in the current directory.
- `-a`: Includes hidden files (those starting with a dot).
- ✅ Confirms the presence of `data.txt`.

---

### 2. 📖 View the contents of the file
```bash
cat data.txt
```
- `cat`: Displays the entire content of a file.
- ✅ Reveals a long list of words or entries.

---

### 3. 🔎 Search for the keyword `millionth`
```bash
grep millionth data.txt
```
- `grep`: Searches for lines containing a specific pattern.
- `millionth`: The target word.
- ✅ Returns the line containing `millionth` and the password next to it.

> **Password found:** `dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc`

---

## 🛠️ Commands You Might Need (Explained)

These commands are listed in the challenge hint and may be useful in other levels:

| Command    | Purpose |
|------------|--------|
| `man`      | Opens the manual page for any command (e.g., `man grep`) |
| `grep`     | Searches for patterns in files |
| `sort`     | Sorts lines in a file alphabetically or numerically |
| `uniq`     | Filters out repeated lines (often used after `sort`) |
| `strings`  | Extracts readable text from binary files |
| `base64`   | Encodes/decodes base64 data |
| `tr`       | Translates or deletes characters (e.g., `tr -d '\n'`) |
| `tar`      | Archives multiple files into one `.tar` file |
| `gzip`     | Compresses files using `.gz` format |
| `bzip2`    | Compresses files using `.bz2` format |
| `xxd`      | Creates a hex dump or converts hex back to binary |

---

## ✅ Summary

- **Challenge solved using:**  
  - `ls -a` → to locate `data.txt`  
  - `cat data.txt` → to inspect its contents  
  - `grep millionth data.txt` → to extract the password

- **Password for Level 8:**  
  ```
  dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
  ```

---

---

# 🔧 Linux Command Reference

## 📖 1. `man`
- **Meaning**: Manual pages (documentation for commands).
- **Working**: Displays detailed help, syntax, options, and examples for any command.
- **Syntax**:
  ```bash
  man <command>
  ```
- **Example**:
  ```bash
  man grep
  ```
  → Opens the manual page for `grep`.

---

## 🔍 2. `grep`
- **Meaning**: Global Regular Expression Print.
- **Working**: Searches for patterns (words, regex) in files and prints matching lines.
- **Syntax**:
  ```bash
  grep [options] "pattern" filename
  ```
- **Useful Options**:
  - `-i` → Ignore case
  - `-n` → Show line numbers
  - `-r` → Recursive search in directories
- **Example**:
  ```bash
  grep -n "error" logfile.txt
  ```

---

## 📑 3. `sort`
- **Meaning**: Sorts lines of text files.
- **Working**: Arranges lines alphabetically, numerically, or by custom rules.
- **Syntax**:
  ```bash
  sort [options] filename
  ```
- **Useful Options**:
  - `-n` → Numeric sort
  - `-r` → Reverse order
  - `-u` → Unique sort (removes duplicates)
- **Example**:
  ```bash
  sort -n numbers.txt
  ```

---

## 🔁 4. `uniq`
- **Meaning**: Filters out adjacent duplicate lines.
- **Working**: Works best on **sorted files**.
- **Syntax**:
  ```bash
  uniq [options] filename
  ```
- **Useful Options**:
  - `-c` → Count occurrences
  - `-d` → Show only duplicates
  - `-u` → Show only unique lines
- **Example**:
  ```bash
  sort data.txt | uniq -c
  ```

---

## 🧵 5. `strings`
- **Meaning**: Extracts human-readable text from binary files.
- **Working**: Scans for printable ASCII sequences inside executables or data files.
- **Syntax**:
  ```bash
  strings [options] filename
  ```
- **Example**:
  ```bash
  strings binaryfile | grep "password"
  ```

---

## 🔐 6. `base64`
- **Meaning**: Encode/Decode data in Base64 format.
- **Working**: Converts binary data into ASCII text (and back).
- **Syntax**:
  ```bash
  base64 [options] filename
  ```
- **Useful Options**:
  - `-d` → Decode
- **Examples**:
  ```bash
  echo "hello" | base64
  echo "aGVsbG8=" | base64 -d
  ```

---

## 🔤 7. `tr`
- **Meaning**: Translate or delete characters.
- **Working**: Reads from stdin, outputs transformed text.
- **Syntax**:
  ```bash
  tr [options] SET1 [SET2]
  ```
- **Useful Options**:
  - `-d` → Delete characters
  - `-s` → Squeeze repeated characters
- **Examples**:
  ```bash
  echo "hello" | tr a-z A-Z
  echo "122333" | tr -s '3'
  ```

---

## 📦 8. `tar`
- **Meaning**: Tape Archive (bundles files).
- **Working**: Creates/extracts `.tar` archives.
- **Syntax**:
  ```bash
  tar [options] archive.tar files
  ```
- **Useful Options**:
  - `-c` → Create archive
  - `-x` → Extract archive
  - `-t` → List contents
  - `-z` → Use gzip compression
  - `-j` → Use bzip2 compression
- **Examples**:
  ```bash
  tar -cvf archive.tar file1 file2
  tar -xvf archive.tar
  ```

---

## 🗜️ 9. `gzip`
- **Meaning**: GNU Zip compression.
- **Working**: Compresses single files into `.gz`.
- **Syntax**:
  ```bash
  gzip filename
  gunzip filename.gz
  ```
- **Example**:
  ```bash
  gzip data.txt
  gunzip data.txt.gz
  ```

---

## 🗜️ 10. `bzip2`
- **Meaning**: High-ratio compression using Burrows-Wheeler algorithm.
- **Working**: Compresses files into `.bz2`.
- **Syntax**:
  ```bash
  bzip2 filename
  bunzip2 filename.bz2
  ```
- **Example**:
  ```bash
  bzip2 report.txt
  bunzip2 report.txt.bz2
  ```

---

## 🔢 11. `xxd`
- **Meaning**: Creates hex dumps and reverses them.
- **Working**: Converts binary → hex (and back).
- **Syntax**:
  ```bash
  xxd [options] filename
  ```
- **Useful Options**:
  - `-r` → Reverse (hex → binary)
  - `-p` → Plain hex output
- **Examples**:
  ```bash
  xxd file.bin | head
  xxd -r hex.txt > file.bin
  ```

---

# ✅ Summary Table

| Command  | Purpose |
|----------|---------|
| `man`    | Show manual pages for commands |
| `grep`   | Search for patterns in files |
| `sort`   | Sort lines of text |
| `uniq`   | Remove/filter duplicate lines |
| `strings`| Extract readable text from binaries |
| `base64` | Encode/Decode Base64 data |
| `tr`     | Translate/delete characters |
| `tar`    | Archive multiple files |
| `gzip`   | Compress files (`.gz`) |
| `bzip2`  | Compress files (`.bz2`) |
| `xxd`    | Hex dump and reverse |

---


