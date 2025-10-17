
## 🎯 Challenge: Bandit Level 10 → Level 11

### 📌 Level Goal  
> The password for the next level is stored in the file `data.txt`, which contains **Base64 encoded data**.

---

## 🧭 Step‑by‑Step Solution

### 1. Inspect the file
```bash
ls -a
```
- Lists all files in the current directory.  
- Confirms that `data.txt` exists.

```bash
cat data.txt
```
- Displays the contents of `data.txt`.  
- The output looks like a long string of letters, numbers, `+`, `/`, and `=` at the end — a clear sign of **Base64 encoding**.

---

### 2. Decode the Base64 content
```bash
base64 -d data.txt
```
- `base64` → command to encode/decode Base64 data.  
- `-d` → tells it to **decode**.  
- `data.txt` → the file containing the encoded string.  

Output:
```
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```

---

## 🔧 Commands Explained

| Command     | Purpose |
|-------------|---------|
| `cat`       | Displays the contents of a file |
| `base64 -d` | Decodes Base64 encoded data back into readable text |

---

## ✅ Summary

- **Challenge solved using:**  
  ```bash
  base64 -d data.txt
  ```
- **Password for Level 11:**  
  ```
  dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
  ```

---
