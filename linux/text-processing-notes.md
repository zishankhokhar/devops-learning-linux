markdown
# Task – Text Processing (grep, awk, sed, pipes & filters)

## 📌 Overview
This task covers the essential Linux text‑processing tools used in real DevOps work:
- Searching text with `grep`
- Extracting fields with `awk`
- Editing text with `sed`
- Using pipes (`|`) to chain commands
- Filtering logs and structured data

---

## 🧩 1. Searching Text with grep

`grep` searches for patterns inside files or command output.

### Basic usage
```bash
grep "error" logfile.txt
Useful options
-i → ignore case

-r → recursive search

-n → show line numbers

-v → show lines NOT matching

Examples
grep -i "failed" /var/log/auth.log
grep -rn "password" .
grep -v "INFO" app.log

🧩 2. Extracting Columns with awk

awk is ideal for structured text (CSV, logs, whitespace‑separated fields).
Print the first column
awk '{print $1}' file.txt

Print multiple columns
awk '{print $1, $3}' file.txt

Filter rows
awk '$3 > 50' data.txt

Real example (show usernames)
awk -F: '{print $1}' /etc/passwd

🧩 3. Editing Text with sed
sed edits text as it streams through the command.

Replace text
sed 's/error/warning/' file.txt

Replace globally on each line
sed 's/foo/bar/g' file.txt

Delete lines
sed '/DEBUG/d' app.log

Insert text before a match
sed '/server/ i\NEW LINE HERE' config.txt

🧩 4. Using Pipes (|)
Pipes send the output of one command into another.

Examples
ls -l | grep ".sh"
ps aux | grep nginx
cat app.log | grep ERROR | wc -l

Real DevOps example
Count failed SSH logins:

grep "Failed password" /var/log/auth.log | wc -l

🧩 5. Combining Tools (Filters)
Extract IP addresses from logs
grep "Failed password" auth.log | awk '{print $11}'

Show top 5 most common IPs
grep "Failed password" auth.log | awk '{print $11}' | sort | uniq -c | sort -nr | head

Remove blank lines
grep -v '^$' file.txt

🧩 6. Useful Commands Summary
Tool	Purpose
grep	Search for text patterns
awk	Extract and process fields
sed	Edit text streams
sort	Sort lines
uniq	Remove duplicates
wc	Count lines/words
cut	Extract columns
tr	Replace characters


🧩 7. Real‑World DevOps Examples
Find all .conf files containing “timeout”
grep -r "timeout" /etc/*.conf

Extract CPU usage from top output
top -b -n1 | grep "Cpu"

Clean JSON logs (remove timestamps)
sed 's/^[0-9:-]* //' logs.json

Monitor logs in real time
tail -f /var/log/syslog | grep ERROR

🧩 8. Quick Cheatsheet
grep "text" file → search

awk '{print $2}' → print column

sed 's/a/b/' → replace

cmd1 | cmd2 → pipe output

sort | uniq -c → count unique items

wc -l → count lines