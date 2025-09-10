# CTF
Writeups of CTF
 📌 Challenge Overview
- **Name:**   FANTASY CTF
- **Category:** General Skills  
- **Platform:** picoCTF  
- **Objective:** Familiarize with terminal-based interaction and basic CTF rules  
- **Flag:** `picoCTF{m1113n1um_3d1710n_1e2b417a}`

---

### 🧠 Challenge Summary
This was a beginner-friendly interactive terminal game designed to introduce players to the picoCTF environment. It emphasized:
- Terminal navigation
- Reading and understanding in-game prompts
- Answering questions based on provided story content

---

### 🛠️ Steps to Solve

#### 1. **Connecting to the Web Shell**
Used `netcat` to connect to the challenge server:
```bash
nc verbal-sleep.picoctf.net 59334
```

#### 2. **Interactive Story Begins**
- The terminal displayed a short narrative.
- I progressed through the story by pressing `Enter` repeatedly.
- The story was designed to be engaging and educational, subtly introducing CTF concepts and rules.

#### 3. **Quiz Phase**
- After the story, a multiple-choice question was presented.
- The question was based on the content of the story.
- I carefully read the options and selected the correct one.

#### 4. **Flag Reveal**
- Upon submitting the correct answer, the game concluded.
- The flag was displayed:
  ```
  picoCTF{m1113n1um_3d1710n_1e2b417a}
  ```

---

### 🧩 Key Takeaways
- **Terminal familiarity** is essential in CTFs—especially for remote shell challenges.
- **Reading comprehension** plays a big role even in technical games.
- **Netcat (`nc`)** is a powerful tool for interacting with remote services.
- This challenge was a great warm-up for more advanced tasks involving shell interaction and logic traps.

---

### 🧠 Reflection
This challenge was a smooth entry point into the picoCTF ecosystem. It reinforced the importance of attentiveness and precision, even in seemingly simple tasks. For newcomers, it’s a great reminder that every detail matters—and for veterans, it’s a quick refresher on terminal-based interaction.


