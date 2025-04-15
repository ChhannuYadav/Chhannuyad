# Core components of a Linux Machine

```plaintext
+----------------------------------------------------+
| User Applications (Vim, Docker, Apache, etc.)     |
+----------------------------------------------------+
| Shell (Bash, Zsh, Fish, etc.)                     |  <-- Part of the OS
+----------------------------------------------------+
| System Libraries (glibc, libc, OpenSSL, etc.)     |  <-- Part of the OS
+----------------------------------------------------+
| System Utilities (ls, grep, systemctl, etc.)      |  <-- Part of the OS
+----------------------------------------------------+
| Linux Kernel (Process, Memory, FS, Network)       |  <-- Core of the OS
+----------------------------------------------------+
| Hardware (CPU, RAM, Disk, Network, Peripherals)   |
+----------------------------------------------------+


(a) Hardware Layer

🔹 The physical components of the computer (CPU, RAM, disk, network interfaces, etc.).
🔹 The OS interacts with hardware using device drivers.
(b) Kernel (Core of Linux OS)

🔹 The Linux Kernel is responsible for directly managing system resources, including:

    Process Management – Schedules processes and handles multitasking.

    Memory Management – Allocates and deallocates RAM efficiently.

    Device Drivers – Acts as an interface between software and hardware.

    File System Management – Manages how data is stored and retrieved.

    Network Management – Handles communication between systems.

(c) Shell (Command Line Interface - CLI)

🔹 A command interpreter that allows users to interact with the kernel.
🔹 Examples: Bash, Zsh, Fish, Dash, Ksh.
🔹 Converts user commands into system calls for the kernel.
(d) User Applications

🔹 End-user programs like web browsers, text editors, DevOps tools, etc.
🔹 Applications interact with the OS using system calls via the shell or GUI.

**Distribution**
# Linux Distributions

Linux distributions (distros) are different versions of Linux that package the Linux kernel with various software, system utilities, and package managers. Each distro is designed for different use cases, such as personal computing, server management, or security.

Here are some popular Linux distributions:

    Ubuntu – One of the most beginner-friendly distros, widely used for personal and server use. It has great community support.

    CentOS (discontinued, replaced by AlmaLinux/Rocky Linux) – Previously a popular choice for servers, based on Red Hat Enterprise Linux (RHEL).

    Debian – A very stable and reliable distro, often used as a base for other distros like Ubuntu.

    Fedora – A cutting-edge distro that introduces new features before they reach RHEL.

    Arch Linux – A lightweight, rolling-release distro for advanced users who like customization.

    Kali Linux – Designed for cybersecurity and penetration testing.

    Alpine Linux – A lightweight, security-focused distro often used in containers.


### Useful References:

- Linux Kernel Source code:
http://git.kernel.org/

- Mirror of Linux Kernel on GitHub:
http://github.com/torvalds/linux

