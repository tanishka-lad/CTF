 
## 🎯 Challenge: Bandit Level 8 → Level 9

### 📌 Level Goal  
> The password for the next level is stored in the file `data.txt` and is the **only line of text that occurs only once**.

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
- You’ll notice it contains a **huge list of repeated lines**.

---

### 2. Sort the file
```bash
sort data.txt
```
- `sort` arranges all lines in order.  
- This step is crucial because `uniq` only works on **adjacent duplicates**.  
- Sorting ensures identical lines are grouped together.

---

### 3. Filter unique lines
```bash
uniq -u
```
- `uniq` filters out repeated lines.  
- `-u` option prints only the lines that appear **once**.  
- When combined with `sort`, this isolates the password.

---

### 4. Combine with a pipeline
```bash
sort data.txt | uniq -u
```
- `|` (pipe) sends the output of `sort` directly into `uniq`.  
- This one‑liner efficiently finds the single unique line in the file.  
- ✅ That line is the **password for the next level**.

---

## 🔧 Commands Explained

| Command | Purpose | Example |
|---------|---------|---------|
| `sort`  | Orders lines alphabetically/numerically so duplicates are adjacent | `sort data.txt` |
| `uniq`  | Removes or filters adjacent duplicates | `uniq -u data.txt` |
| `uniq -u` | Shows only lines that occur once | `sort data.txt \| uniq -u` |
| `|` (pipe) | Redirects output of one command into another | `cmd1 \| cmd2` |

---

## ✅ Summary

- **Challenge solved using:**  
  ```bash
  sort data.txt | uniq -u
  ```
- **Password for Level 9:**  
  ```
  4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
  ```

---

