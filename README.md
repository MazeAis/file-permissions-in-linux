# 🐧 Linux File Permissions Demonstration

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

## 🔧 Step 2: Removing Write Access for "Other"
The requirement: Remove write permissions for anyone not the owner or in the group.

![](https://i.imgur.com/EqfN9Gx.png)

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
Now, "other" users can only read but not write.

## 📂 Step 3: Changing Permissions for a Hidden File

![](https://i.imgur.com/hlDxgSy.png)

Hidden files in Linux start with a dot (.). For example: .hiddenfile.

The requirement: Give the owner read/write, group read-only, and remove all permissions for others.

Command used:
```bash
chmod u-w,g-w,g+r .hiddenfile
```
Verification:
```bash
ls -la .hiddenfile
```
Result:
```bash
-rw-r----- 1 user user 5678 Aug 10 12:35 .hiddenfile
```

## 🛡️ Step 4: Restricting Directory Access
The requirement: Allow only the owner to read, write, and execute in the directory. No access for group or others.

![](https://i.imgur.com/WC9TGna.png)

Command used:
```bash
chmod g-x my_folder
```
Verification:
```bash
ls -ld my_folder
```
Result:
```bash
drwx------ 2 user user 4096 Aug 10 12:36 my_folder
```


##  📚Summary

Conducted a thorough review and adjustment of file and directory permissions within the projects directory to enforce the principle of least privilege and strengthen access controls. Utilized the ls -la command to perform detailed permission audits, then applied chmod commands to remediate permission gaps, reducing potential security risks related to unauthorized access.
