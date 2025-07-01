# 🔍 How to Find Files and Manage Permissions in Linux

---

## ✅ Understanding Permissions in Linux

When we check file or directory permissions using:

ls -l

The output looks like this:

drwxr-xr-x

🔸 Explanation:

| Symbol | Meaning                                  |
| ------ | ---------------------------------------- |
| **d**  | Directory (If it’s a file, it shows `-`) |
| **r**  | Read  → Value = **4**                    |
| **w**  | Write → Value = **2**                    |
| **x**  | Execute → Value = **1**                  |

🔸 Permission Structure:

It has 3 sections (groups):

| Section    | Meaning                     | Example Permission | Value Calculation |
| ---------- | --------------------------- | ------------------ | ----------------- |
| **User**   | Owner of the file/directory | rwx                | 4+2+1 = **7**     |
| **Group**  | Group members               | r-x                | 4+0+1 = **5**     |
| **Others** | Everyone else               | r-x                | 4+0+1 = **5**     |

Example:

drwxr-xr-x → Permission = 755

→ This means the owner has full permissions, while group and others have read & execute only.

🔥 Give Full Permissions (777):

For directories:

chmod -R 777 d1


For files:

chmod 777 f1

⚠️ Note:
If you remove permissions for the user, the user won’t be able to access that file or directory.
Example: If permission is set to 000, it means no one has any permission, and you’ll get Permission denied.

✅ Check Disk and Memory Usage

| Command   | Purpose                                  |
| --------- | ---------------------------------------- |
| `du -sh`  | Show the **size of the current folder**. |
| `du -sh *`| Show the ** size of all dir & files**.   |
| `df -h`   | Check **disk size and free space**.      |
| `free -m` | Check **system memory (RAM)** usage.     |

🔸 Explanation of du -sh:

d → Disk

u → Usage

s → Size

h → Human-readable format

✅ Echo Command — Print Statements

| Command                       | Purpose                                   |
| ----------------------------- | ----------------------------------------- |
| `echo 'Good Evening'`         | Print message in terminal.                |
| `echo 'Good Evening' > file1` | Print into a **file** (overwrite).        |
| `echo 'Hello' >> file1`       | **Append** to a file (without overwrite). |
| `echo -e 'Good \t Evening'`   | Print with **tab space** between words.   |
| `echo -e 'Good \n Evening'`   | Print on **new lines**.                   |

✅ Find Command — Locate Files and Directories

| Command                          | Purpose                                  |
| -------------------------------- | ---------------------------------------- |
| `find . -type f -iname filename` | Find a **file** (case-insensitive).      |
| `find . -type d -iname dirname`  | Find a **directory** (case-insensitive). |

🔥 Find Based on Time:

| Command                     | Purpose                                        |
| --------------------------- | ---------------------------------------------- |
| `find . -type f -mtime +90` | Files modified **more than 90 days ago**.      |
| `find . -type f -mtime -90` | Files modified **within the last 90 days**.    |
| `find . -type f -mmin +10`  | Files modified **more than 10 minutes ago**.   |
| `find . -type f -mmin -10`  | Files modified **within the last 10 minutes**. |

✅ Rename Files

| Command              | Purpose                            |
| -------------------- | ---------------------------------- |
| `mv oldname newname` | Rename file. Example: `mv f4 f007` |

✅ Check Command History

| Command      | Purpose                                      |
| ------------ | -------------------------------------------- |
| `history`    | Display all commands you have used so far.   |
| `!number`    | Run a command from history using its number. |
| `history -c` | **Clear** the history (current session).     |

✅ Summary of Useful Commands

| Task                            | Command Example                  |
| ------------------------------- | -------------------------------- |
| Check permissions               | `ls -l`                          |
| Change permissions (folder)     | `chmod -R 777 d1`                |
| Change permissions (file)       | `chmod 777 file1`                |
| Check folder size               | `du -sh`                         |
| Check disk usage                | `df -h`                          |
| Check memory                    | `free -m`                        |
| Print statement                 | `echo 'Hello'`                   |
| Print into a file               | `echo 'Hello' > file1`           |
| Append to a file                | `echo 'Welcome' >> file1`        |
| Find a file                     | `find . -type f -iname filename` |
| Find a directory                | `find . -type d -iname dirname`  |
| Find files modified 90 days ago | `find . -type f -mtime +90`      |
| Rename file                     | `mv oldname newname`             |
| Show history                    | `history`                        |
| Clear history                   | `history -c`                     |
