# VI Editor Shortcuts 

### Modes in VI Editor
- **Normal Mode** (default) – Used for navigation and command execution.
- **Insert Mode** – Used for text editing (press `i` to enter, `Esc` to exit).
- **Command Mode** – Used for saving, quitting, and searching (press `:` in Normal mode).

---

### Basic Navigation
- `h` – Move **left**  
- `l` – Move **right**  
- `j` – Move **down**  
- `k` – Move **up**  
- `0` – Move to the **beginning** of the line  
- `^` – Move to the **first non-blank** character of the line  
- `$` – Move to the **end** of the line  
- `w` – Move to the **next word**  
- `b` – Move to the **previous word**  
- `gg` – Move to the **start** of the file  
- `G` – Move to the **end** of the file  
- `:n` – Move to **line number `n`**  

---

### Insert Mode Shortcuts
- `i` – Insert before cursor  
- `I` – Insert at the beginning of the line  
- `a` – Append after cursor  
- `A` – Append at the end of the line  
- `o` – Open a new line below  
- `O` – Open a new line above  
- `Esc` – Exit insert mode  

---

### Editing Text
- `x` – Delete a **character**  
- `X` – Delete a **character before cursor**  
- `dw` – Delete a **word**  
- `dd` – Delete a **line**  
- `d$` – Delete from **cursor to end of line**  
- `d0` – Delete from **cursor to beginning of line**  
- `D` – Delete from **cursor to end of line**  
- `u` – **Undo** last action  
- `Ctrl + r` – **Redo** an undone change  
- `yy` – Copy (yank) a **line**  
- `yw` – Copy (yank) a **word**  
- `p` – Paste **after** the cursor  
- `P` – Paste **before** the cursor  

---

### Search and Replace
- `/pattern` – Search **forward** for a pattern  
- `?pattern` – Search **backward** for a pattern  
- `n` – Repeat last search **forward**  
- `N` – Repeat last search **backward**  
- `:%s/old/new/g` – Replace **all occurrences** of "old" with "new"  
- `:s/old/new/g` – Replace **all occurrences** in the current line  

---

### Working with Multiple Files
- `:e filename` – Open a **new file**  
- `:w` – Save file  
- `:wq` – Save and exit  
- `:q!` – Quit **without saving**  
- `:split filename` – Split screen **horizontally** and open another file  
- `:vsplit filename` – Split screen **vertically**  
- `Ctrl + w + w` – Switch between split screens  

---
# File Permissions Management in Linux

## Introduction to File Permissions
Linux file permissions determine who can read, write, or execute files and directories. Each file and directory has three levels of permission:
- **Owner (User)**: The creator of the file.
- **Group**: Users belonging to the assigned group.
- **Others**: All other users on the system.

Permissions are represented as:
- **Read (`r` or `4`)** – View file contents.
- **Write (`w` or `2`)** – Modify file contents.
- **Execute (`x` or `1`)** – Run scripts or programs.

To check file permissions, use:
```bash
ls -l filename
```
Output example:
```bash
-rwxr--r-- 1 user group 1234 Mar 28 10:00 myfile.sh
```

## Changing Permissions with `chmod`
### Using Symbolic Mode
Modify permissions using symbols:
- Add (`+`), remove (`-`), or set (`=`) permissions.

Examples:
```bash
chmod u+x filename  # Add execute for user
chmod g-w filename  # Remove write for group
chmod o=r filename  # Set read-only for others
chmod u=rwx,g=rx,o= filename  # Set full access for user, read/execute for group, and no access for others
```

### Using Numeric (Octal) Mode
Each permission has a value:
- Read (`4`), Write (`2`), Execute (`1`).

Examples:
```bash
chmod 755 filename  # User (rwx), Group (r-x), Others (r-x)
chmod 644 filename  # User (rw-), Group (r--), Others (r--)
chmod 700 filename  # User (rwx), No access for others
```

## Changing Ownership with `chown`
Modify file owner and group:
```bash
chown newuser filename  # Change owner
chown newuser:newgroup filename  # Change owner and group
chown :newgroup filename  # Change only group
```

Recursively change ownership:
```bash
chown -R newuser:newgroup directory/
```

## Changing Group Ownership with `chgrp`
```bash
chgrp newgroup filename  # Change group
chgrp -R newgroup directory/  # Change group recursively
```

## Special Permissions
### SetUID (`s` on user execute bit)
Allows users to run a file with the file owner's permissions.
```bash
chmod u+s filename
```
Example: `/usr/bin/passwd` allows users to change their passwords.

### SetGID (`s` on group execute bit)
Files: Users run the file with the group's permissions.
Directories: Files created inside inherit the group.
```bash
chmod g+s filename  # Set on file
chmod g+s directory/  # Set on directory
```

### Sticky Bit (`t` on others execute bit)
Used on directories to allow only the owner to delete their files.
```bash
chmod +t directory/
```
Example: `/tmp` directory.

## Default Permissions: `umask`
`umask` defines default permissions for new files and directories.
Check current umask:
```bash
umask
```
Set a new umask:
```bash
umask 022  # Default: 755 for directories, 644 for files
```

## Conclusion
Understanding file permissions is essential for system security and proper file management. Using `chmod`, `chown`, and `chgrp`, you can control access to files and directories efficiently.

# Process Management in Linux

## Introduction to Process Management
A process is an instance of a running program. Linux provides multiple utilities to monitor, manage, and control processes effectively. Each process has a unique **Process ID (PID)** and belongs to a parent process.

## Index of Commands Covered

### Viewing Processes
- `ps aux` – View all running processes
- `ps -u username` – View processes for a specific user
- `ps -C processname` – Show a process by name
- `pgrep processname` – Find a process by name and return its PID
- `pidof processname` – Find the PID of a running program

### Managing Processes
- `kill PID` – Terminate a process by PID
- `pkill processname` – Terminate a process by name
- `kill -9 PID` – Force kill a process
- `pkill -9 processname` – Kill all instances of a process
- `kill -STOP PID` – Stop a running process
- `kill -CONT PID` – Resume a stopped process
- `renice -n 10 -p PID` – Lower priority of a process
- `renice -n -5 -p PID` – Increase priority of a process (requires root)

### Background & Foreground Processes
- `command &` – Run a command in the background
- `jobs` – List background jobs
- `fg %jobnumber` – Bring a job to the foreground
- `Ctrl + Z` – Suspend a running process
- `bg %jobnumber` – Resume a suspended process in the background

### Monitoring System Processes
- `top` – Interactive process viewer
- `htop` – User-friendly process viewer (requires installation)
- `nice -n 10 command` – Run a command with a specific priority
- `renice -n -5 -p PID` – Change priority of an existing process

### Daemon Process Management
- `systemctl list-units --type=service` – List all system daemons
- `systemctl start service-name` – Start a daemon/service
- `systemctl stop service-name` – Stop a daemon/service
- `systemctl enable service-name` – Enable a service at startup

## Viewing Process Details
### Using `ps`
Show processes for a specific user:
```bash
ps -u username
```
Show a process by name:
```bash
ps -C processname
```

### Using `pgrep`
Find a process by name and return its PID:
```bash
pgrep processname
```

### Using `pidof`
Find the PID of a running program:
```bash
pidof processname
```

## Managing Processes
### Killing Processes
To terminate a process by PID:
```bash
kill PID
```
To terminate using process name:
```bash
pkill processname
```
Force kill a process:
```bash
kill -9 PID
```
Kill all instances of a process:
```bash
pkill -9 processname
```

### Stopping & Resuming Processes
Stop a running process:
```bash
kill -STOP PID
```
Resume a stopped process:
```bash
kill -CONT PID
```

### Changing Process Priority
View process priorities:
```bash
top  # Look at the NI column
```
Change priority of a running process:
```bash
renice -n 10 -p PID  # Lower priority (positive values)
renice -n -5 -p PID  # Higher priority (negative values, root required)
```

### Running Processes in the Background
Run a command in the background:
```bash
command &
```
List background jobs:
```bash
jobs
```
Bring a job to the foreground:
```bash
fg %jobnumber
```
Send a running process to the background:
```bash
Ctrl + Z  # Suspend process
bg %jobnumber  # Resume in background
```

## Monitoring System Processes
### Using `top`
Interactive process viewer:
- Press `k` and enter a PID to kill a process.
- Press `r` to renice a process.
- Press `q` to quit.

### Using `htop`
A user-friendly alternative to `top`:
```bash
htop
```
Allows mouse-based interaction for process management.

### Using `nice` & `renice`
Run a command with a specific priority:
```bash
nice -n 10 command
```
Change the priority of an existing process:
```bash
renice -n -5 -p PID
```

## Daemon Processes
Daemon processes run in the background without user intervention.
List all system daemons:
```bash
systemctl list-units --type=service
```
Start a daemon:
```bash
systemctl start service-name
```
Stop a daemon:
```bash
systemctl stop service-name
```
Enable a service at startup:
```bash
systemctl enable service-name
```

## Conclusion
Process management is crucial for system performance and stability. By using tools like `ps`, `top`, `htop`, `kill`, and `nice`, you can efficiently control and monitor Linux processes.
