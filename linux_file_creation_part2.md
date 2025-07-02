# 🔍 Finding Files, Links, Users, and Passwordless SSH — Linux Guide

---

## ✅ Finding Empty Files

| Command                                  | Purpose                                  |
|-------------------------------------------|-------------------------------------------|
| `find . -type f -empty`                   | Find **empty files** in the current directory and subdirectories.|

---

## ✅ Finding Files Based on Permissions

| Command                                  | Purpose                                  |
|-------------------------------------------|-------------------------------------------|
| `find . -type f -perm 777`                | Find files that have **full permissions (read, write, execute) for user, group, and others**.|

---

## ✅ Finding Files Based on Size

| Command                                   | Purpose                                  |
|--------------------------------------------|-------------------------------------------|
| `find . -type f -size -4k`                 | Find files that are **less than 4 KB**.   |
| `find . -type f -size +4k`                 | Find files that are **greater than or equal to 4 KB**.|

---

## 🔗 Link — What is a Link?

A **link** is like a shortcut to a file.

→ If any changes are made in the link, the **original file also gets modified**, and vice versa (because both point to the same data on disk).

There are **two types of links in Linux:**

---

### 🔸 **1) Soft Link (Symbolic Link)**

| Description                                     |
|-------------------------------------------------|
| - Acts like a shortcut to the original file.    |
| - If the original file is deleted, **the link breaks** (shows error). |
| - Changes made to the link reflect in the original file.|

| Command Example:                                |
|-------------------------------------------------|
| `ln -s filename linkname`                       |

---

### 🔸 **2) Hard Link**

| Description                                     |
|-------------------------------------------------|
| - It directly points to the data on disk.       |
| - If the **original file is deleted, the link still works.** |
| - Both the link and the original are equally valid; there is no 'main' or 'copy'.|

| Command Example:                                |
|-------------------------------------------------|
| `ln filename linkname`                          |

---

## ✅ User Management Commands

| Command                                        | Purpose                                  |
|-------------------------------------------------|-------------------------------------------|
| `useradd -m username`                          | Create a user. `-m` creates a home directory for the user. |
| `passwd username`                              | Set or change the password for a user.   |
| `su username`                                  | Switch to another user.                  |
| `exit`                                         | Logout from the current user session.    |

---

## ✅ System Information Commands

| Command          | Purpose                                   |
|------------------|-------------------------------------------|
| `uname -v`       | Show the kernel version.                 |
| `uname -a`       | Show **all system information**.         |
| `hostname`       | Display the hostname (server name).      |
| `hostname -i`    | Display the IP address of the server.    |
| `hostname -f`    | Display the **Fully Qualified Domain Name (FQDN)**.|

---

## 🔐 How to Create Passwordless SSH Connection Between Two Servers

### ✅ **Steps:**

1️⃣ **On the main server (Server 1), generate an SSH key pair:**


ssh-keygen

This creates:

A private key: ~/.ssh/id_rsa

A public key: ~/.ssh/id_rsa.pub

2️⃣ Copy the public key to Server 2:

Either manually:

cat ~/.ssh/id_rsa.pub

Copy the output.

On Server 2, open or create the file:

vim ~/.ssh/authorized_keys

Paste the public key content into it.

Or use the easy method:

ssh-copy-id username@server2_ip_address

3️⃣ Test SSH from Server 1 to Server 2:

ssh username@server2_ip_address

→ You should now be able to connect without a password.

🚀 Summary of Important Commands

| Task                                 | Command Example                   |
| ------------------------------------ | --------------------------------- |
| Find empty files                     | `find . -type f -empty`           |
| Find files with 777 permission       | `find . -type f -perm 777`        |
| Find files less than 4KB             | `find . -type f -size -4k`        |
| Find files greater than or equal 4KB | `find . -type f -size +4k`        |
| Create soft link                     | `ln -s filename linkname`         |
| Create hard link                     | `ln filename linkname`            |
| Create user                          | `useradd -m username`             |
| Set user password                    | `passwd username`                 |
| Switch user                          | `su username`                     |
| Logout user                          | `exit`                            |
| Get system info                      | `uname -a`                        |
| Get hostname                         | `hostname`                        |
| Get IP address                       | `hostname -i`                     |
| Fully qualified hostname             | `hostname -f`                     |
| Generate SSH keys                    | `ssh-keygen`                      |
| Copy SSH keys to another server      | `ssh-copy-id username@server2_ip` |
| Connect to another server via SSH    | `ssh username@server2_ip`         |
