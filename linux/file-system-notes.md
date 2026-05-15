# File system notes

## 5 useful commands

1. `ls -lah`  
   - Lists files in the current directory with:
     - `-l`: long format (permissions, owner, size, date)
     - `-a`: show hidden files
     - `-h`: human-readable sizes

2. `cd /var/log`  
   - Changes directory to `/var/log`, where many system log files live.

3. `tail -f /var/log/auth.log`  
   - Shows the end of the file and follows new lines in real time (useful for watching logins).

4. `head -n 20 /etc/services`  
   - Prints the first 20 lines of `/etc/services`.

5. `less /var/log/syslog`  
   - Opens the file in a pager so you can scroll up/down (`q` to quit).
