# 🐧 Linux File Permissions Project

## 📌 Objective
The goal of this project was to explore, understand, and modify file and directory permissions in a Linux environment, gaining hands-on experience with permission structures, the `chmod` command, and security best practices.

---

## 🔍 Step 1: Viewing File Permissions

![](https://i.imgur.com/VAd3U6U.png)

To check file and directory permissions in Linux, the `ls -la` command was used:

```bash
ls -la
```
Example output:
```bash
-rw-rw-r-- 1 user user  1234 Aug 10 12:34 example.txt
drwxrwxr-x 2 user user  4096 Aug 10 12:34 my_folder
```
Understanding the Permission String
The permission string (e.g., -rw-rw-r--) is broken down as follows:
| Position | Meaning                                     | Example |
| -------- | ------------------------------------------- | ------- |
| 1        | File type (`-` for file, `d` for directory) | `-`     |
| 2-4      | Owner permissions                           | `rw-`   |
| 5-7      | Group permissions                           | `rw-`   |
| 8-10     | Others (public) permissions                 | `r--`   |

Permission Legend

| Symbol | Meaning           |
|--------|-------------------|
| `r`    | Read permission   |
| `w`    | Write permission  |
| `x`    | Execute permission|
| `-`    | No permission     |

🔧 Step 2: Removing Write Access for "Other"
The requirement: Remove write permissions for anyone not the owner or in the group.

Command used:
```bash
chmod o-w example.txt
```
Verification:
```bash
ls -l example.txt
```
Result:
```bash
-rw-rw-r-- 1 user user 1234 Aug 10 12:34 example.txt
```
