# Task 3 – Permissions and Ownership (Linux & macOS)

## 📌 Overview
This task covers:
- Creating and running a shell script  
- Understanding file permissions  
- Changing file ownership (Linux vs macOS differences)  
- Using numeric permissions (e.g., 644)

---

## 🧩 1. Creating and Running a Script

### Commands
```bash
echo '#!/bin/bash' > hello.sh
echo 'echo "Hello DevOps"' >> hello.sh
chmod +x hello.sh
./hello.sh

## What this does
- Creates a new script file
- Adds a print statement
- Makes the script executable
- Runs the script

🧩 2. Understanding Permission Bits
Linux/macOS permissions use three types:

r → read

w → write

x → execute

And three groups:

Owner

Group

Others

Example permission string:
-rwxr-xr--

Breakdown:

Section	Meaning
rwx - Owner can read, write, execute
r-x - Group can read, execute
r--	- Others can read

🧩 3. Changing Ownership

Linux (Bootcamp Example)
Linux has a root user and a root group.

sudo chown root:root hello.sh

macOS (Your System)
macOS does not have a root group → root:root fails.
Correct macOS command:
sudo chown root hello.sh

Check Ownership
ls -l hello.sh

Example Output (macOS)
-rwxr-xr-x  1 root  staff  32  May 15 19:21  hello.sh

Permission Breakdown
Owner (root): rwx
Group (staff): r-x
Others: r-x

🧩 4. Numeric Permissions (chmod)
Numeric permissions use:

4 = read

2 = write

1 = execute


Number	Meaning
7	rwx
6	rw-
5	r-x
4	r--

🧩 5. Challenge: File With rw for Owner, r for Others

touch secure.txt
chmod 644 secure.txt
ls -l secure.txt

What 644 Means
6 → owner: read + write
4 → group: read
4 → others: read

-rw-r--r--  1 zishan  staff  0  May 15 19:25  secure.txt

🧩 6. Summary of Key Commands
Command	Description
chmod	Change file permissions
chown	Change file owner (and group on Linux)
ls -l	View permissions & ownership
./file	Execute a script
touch	Create a fileC 