
---

## 🔐 Bandit Level 6 → Level 7 Writeup

### 🧩 Challenge Description
> The password for the next level is stored somewhere on the server and has all of the following properties:
> - Owned by user `bandit7`
> - Owned by group `bandit6`
> - 33 bytes in size

---

### 🛠️ Strategy
To locate the file, we used the `find` command with filters for:
- File type (`-type f`)
- Exact size (`-size 33c`)
- Owner (`-user bandit7`)
- Group (`-group bandit6`)

---

### 📜 Command Used
```bash
find / -type f -size 33c -user bandit7 -group bandit6 2>/dev/null
```

- `find /` → Search from the root directory
- `-type f` → Look for regular files
- `-size 33c` → Match files exactly 33 bytes
- `-user bandit7` → Owned by user `bandit7`
- `-group bandit6` → Owned by group `bandit6`
- `2>/dev/null` → Suppress permission errors

---

### 🔍 Result
The command returned a file path matching all criteria. We then used:
```bash
cat /path/to/file
```
to read the contents and retrieve the password for Level 7.

---

### ✅ Takeaway
This level teaches how to use `find` effectively with multiple filters and how to handle permission errors gracefully using redirection.

---
Password for level 7 :morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj


**Explaining file ownership**

Okay, I need to explain file ownership and group ownership clearly, while keeping it concise. I can use "File ownership" as the heading, and separate the sections about user and group ownership, with examples like `ls -l`. I’ll avoid parentheses in headings and follow the rule about not asking questions. To explain permissions, I'll mention how to view file ownership with `ls -l` or `stat`, and how to change the owner with `chown`, but note you might not be able to do that in some environments like Bandit.
### File ownership

Every file on a Linux system has an owner and a group. The **owner** is a single user account that “owns” the file. The **group** is a user group that the file belongs to. Ownership determines which users can read, write, or execute the file according to the file’s permission bits.

#### User owner
- The user owner is usually the account that created the file.
- If the user owner is `bandit7`, that means the file’s owner field is set to that user and the “user” permission bits apply to `bandit7`.

#### Group owner
- A group is a named collection of users (for example `bandit6`).
- If the group owner is `bandit6`, then any user who is a member of the `bandit6` group gets the permissions defined in the group bits for that file.

---

### How you see owner and group

Run:
```bash
ls -l filename
```
Typical output:
-rw-r----- 1 bandit7 bandit6 33 Sep 28 23:00 secret.txt

- First column (`-rw-r-----`) are permission bits.
- The field after the link count (`1`) is the **user owner** (`bandit7`).
- The next field is the **group owner** (`bandit6`).
- `33` is the file size in bytes.

You can also get full details with:
```bash
stat filename
```

---

### What ownership affects

- Permissions are split into three sets: user (owner), group, others.
- If owner has `r` (read) permission, that owner can open the file. If group has `r`, any user in that group can open it. If others have no `r`, users outside owner/group cannot read it.
- Ownership does not itself grant or deny access; the permission bits combined with owner/group determine access.

---

### Commands that change ownership (requires privileges)
- Change owner and group:
```bash
chown newuser:newgroup filename
```
- Change only group:
```bash
chgrp groupname filename
```

---

### Short summary
- “Owned by user X” = the file’s user owner field is X; user permission bits apply to X.
- “Owned by group Y” = the file’s group owner field is Y; group permission bits apply to members of Y.
- Use `ls -l` or `stat` to check owner and group.


### Clarifying the idea of groups and users

No — being in a group does **not** give you access to another user’s account. Group membership only affects the file and directory permissions that apply to that group.

---

### What group membership actually means
- A **group** is a named collection of user accounts used for permission control.
- If a file is owned by group **flower**, then the file’s **group permission bits** (the middle trio in `rwxrwxrwx`) control what members of the flower group can do with that file.
- Members of group **flower** (rose, lily, lotus) will get whatever access the group bits allow on files owned by group flower.
- Group membership does **not** let rose log in as lotus or read lotus’s files unless those files’ permissions explicitly permit group or others to read them.

---

### Example with ls -l
If you run `ls -l secret.txt` and see:
-rw-r----- 1 lotus flower 33 Sep 28 23:00 secret.txt

- **Owner**: lotus — owner bits (first trio after the dash) apply to lotus.
- **Group**: flower — group bits (second trio) apply to members of flower (rose, lily, lotus).
- **Permissions**: `rw- r-- ---`
  - Owner lotus can read and write.
  - Group members can read.
  - Others have no access.

So rose can read secret.txt because rose is in flower and the group has read permission, but rose cannot log in as lotus or change lotus’s password.

---

### Commands to check groups and membership
- Show groups a user belongs to:
  - groups rose
  - id rose
- Show members of a group:
  - getent group flower

---

### Summary
- Group membership grants access only to resources whose group owner and group permission bits allow it.
- Group membership never grants control of another user account or the ability to authenticate as that user.

