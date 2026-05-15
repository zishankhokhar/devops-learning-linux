# Task 4 – Process Management (Linux & macOS)

## 📌 Overview
This task covers:
- Running background processes  
- Listing active processes  
- Finding specific processes  
- Killing processes using their PID  
- Verifying that a process has stopped  

---

## 🧩 1. Starting a Background Process

### Command
```bash
sleep 300 &

What this does
- sleep 300 → pauses for 300 seconds
- & → runs the command in the background
- The terminal prints a PID (Process ID), e.g.:
[1] 5339

Key point
The PID (e.g., 5339) is the unique identifier for the running process.


🧩 2. Listing Processes

ps aux

### What this shows
- All running processes
- Their CPU/memory usage
- Their PID
- The command that started them

To filter for a specific process:
ps aux | grep sleep

zishan     5339   0.0  ...   sleep 300
zishan     5340   0.0  ...   grep sleep

🧩 3. Killing a Process

Example using your PID:
kill 5339
This sends a SIGTERM (terminate) signal.

If a process refuses to stop:

kill -9 <PID>
This sends SIGKILL (force kill).

🧩 4. Verifying the Process is Gone

ps aux | grep sleep

Expected result
Only the grep line should appear:
zishan   5400   0.0  ...   grep sleep
This confirms the sleep process has been terminated.


## 🧩 5. Useful Process Commands

### Common Process Commands

**Run a process in the background**
```bash
sleep 300 &

List all running processes
ps aux

Search for a specific process
ps aux | grep <name>

Terminate a process
kill <PID>

Force‑kill a process
kill -9 <PID>

Live system monitoring
top

(If installed)
htop
