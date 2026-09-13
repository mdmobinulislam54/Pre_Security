# TryHackMe — Offensive Security Intro

**Path:** Pre Security | **Difficulty:** Easy

## 🔴 What is Offensive Security?

**Offensive Security** means thinking like an attacker and finding weaknesses in a system before a real attacker can exploit them.

**Defensive Security** focuses on protecting systems, detecting attacks, and responding to threats.

```text
Offensive → Find weaknesses
Defensive → Protect against weaknesses
```

---

## Task 1 — Offensive Security

**Question:** Which term describes simulating a hacker's actions to find weaknesses?

**Answer:**

```text
Offensive Security
```

---

## Task 2 — Explore FakeBank

TryHackMe provides a virtual machine containing **FakeBank**, a fake banking website.

The goal is to find a weakness in the application. By opening **View Site** and exploring the website, we can see how a normal user interacts with it.

But websites can also contain pages that aren't visible or linked from the main page.

### 📁 What is a Directory?

A **directory** is a location used to organize files or web resources.

On a website, a directory can contain pages, files, images, or other resources.

For example:

```text
http://fakebank.thm/images
```

Here, `images` is a directory.

Finding directories that aren't linked from the main website is called **directory enumeration**.

There are different ways to perform enumeration, including manually checking common paths or using tools such as **Dirb, Gobuster, and Feroxbuster**.

---

## Task 3 — Find the Hidden Directory

Open the terminal and run:

```bash
dirb http://fakebank.thm

```

Dirb searches the website for common directories and files.

The room tells us that Dirb found:

```text
http://fakebank.thm/images
```

### Question

**What is the other hidden URL?**

**Answer:**

```text
http://fakebank.thm/bank-transfer
```

💥 We found a hidden bank-transfer page.

---

## Task 4 — Complete the Challenge

Open:

```text
http://fakebank.thm/bank-transfer
```

Use account number:

```text
8881
```

Deposit **$2000 or more**.

After the transaction, return to the account page and confirm that the balance is positive.

A popup with **green text** will appear. This is the final answer.

```text
Final Flag: YOUR_FLAG_HERE
```

Replace `YOUR_FLAG_HERE` with the exact green text shown in your TryHackMe lab.

---

## 🧠 What I Learned

* Offensive vs Defensive Security
* What a web directory is
* What directory enumeration means
* How to use **Dirb**
* How hidden pages can expose sensitive functionality

**Room Completed ✅**
