# TryHackMe — Offensive Security Intro

**Path:** Pre Security
**Difficulty:** Easy
**Topic:** Offensive Security & Web Enumeration

## 📝 Overview

This room introduces **Offensive Security**, where we think like an attacker to find weaknesses in systems before real attackers can exploit them.

The practical part uses **FakeBank**, a deliberately vulnerable banking website provided by TryHackMe.

---

## 1. Offensive Security

**Question:** Which term describes simulating a hacker's actions to find weaknesses?

**Answer:**

```text
Offensive Security
```

---

## 2. Finding Hidden Pages

The goal is to find hidden pages on the FakeBank website.

First, open the terminal and use **Dirb**:

```bash
dirb http://fakeba
nk.thm
```

Dirb searches the website for common directories and files.

The scan finds:

```text
http://fakebank.thm/images
http://fakebank.thm/bank-transfer
```

The hidden page we need is:

```text
http://fakebank.thm/bank-transfer
```

---

## 3. Using the Hidden Page

Open `/bank-transfer` in the browser.

Use the account number:

```text
8881
```

Deposit **$2000 or more**.

Then return to the account page and check the balance.

When the balance becomes positive, FakeBank displays a popup containing **green text**.

### Final Answer

Enter the green text shown by your own TryHackMe lab in **ALL CAPS**:

```text
YOUR_FLAG_HERE
```

---

## 🧠 What I Learned

* Offensive Security means testing systems from an attacker's perspective.
* **Dirb** can discover hidden web directories and pages.
* Hidden pages can expose sensitive functionality.
* A page being unlinked from a website does **not** make it secure.
* Security testing should only be performed on systems where you have permission.

## 🛠️ Tool Used

**Dirb** — Web content/directory enumeration.

### Main Command

```bash
dirb http://fakebank.thm
```

**Room:** Completed ✅
