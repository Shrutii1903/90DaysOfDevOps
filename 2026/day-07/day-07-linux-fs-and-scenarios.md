# Linux Filesystem Hierarchy – Detailed Guide
```/ → Root Directory```

What it is: The top-level directory of the Linux filesystem. Everything starts here.

Example: /bin, /home, /var, /etc are all under /.

/bin → Essential User Binaries

Purpose: Contains basic commands that all users need, even in single-user mode.

Examples: ls, cp, mv, cat.

Note: Required for the system to boot and operate minimally.

/sbin → System Binaries

Purpose: Contains commands for system administration, mostly used by root.

Examples: fdisk (partition manager), ifconfig (network config), reboot.

/usr → User Programs and Data

Purpose: Stores most software, libraries, and documentation.

Subdirectories:

/usr/bin → Programs for users (like nano, python).

/usr/sbin → Admin programs (like apache2, cron).

/usr/lib → Libraries needed by binaries.

/etc → Configuration Files

Purpose: Contains system and application configuration files.

Examples:

/etc/passwd → user accounts

/etc/ssh/sshd_config → SSH server config

/etc/crontab → scheduled jobs

/home → User Home Directories

Purpose: Personal workspace for regular users.

Example: /home/alice contains files, documents, and scripts for user alice.

Tip: Always store your work here instead of /root.

/root → Root User Home

Purpose: Personal home directory for the root user.

Note: Only root can write here. Used for admin tasks.

/var → Variable Data

Purpose: Stores files that change frequently during system operation.

Subdirectories:

/var/log → system and service logs

/var/spool → mail, cron jobs, printing queues

/var/tmp → temporary files preserved across reboots

/tmp → Temporary Files

Purpose: Temporary storage for files created by applications.

Note: Usually cleared on reboot. Good for short-lived files.

/dev → Device Files

Purpose: Represents hardware devices as files.

Examples:

/dev/sda → first hard disk

/dev/tty → terminal

/dev/usb → USB devices

/proc → Process Information

Purpose: Virtual filesystem showing real-time info about processes and kernel.

Examples:

/proc/cpuinfo → CPU details

/proc/meminfo → memory info

Note: Not real files; the kernel generates this on the fly.

/sys → Kernel Interface

Purpose: Virtual filesystem for interacting with kernel and devices.

Example: /sys/class/net shows network interfaces.

/mnt → Temporary Mounts

Purpose: Temporary mount points for disks or partitions during maintenance.

Example: sudo mount /dev/sdb1 /mnt to access a disk manually.

/media → Removable Media

Purpose: Mount points for USB drives, CDs, and other removable devices.

Example: /media/usb → USB stick contents.

/opt → Optional Software

Purpose: Contains third-party or optional software packages.

Example: /opt/google/chrome → Google Chrome installed manually.

/lib → Shared Libraries

Purpose: Stores essential libraries required by system binaries in /bin and /sbin.

Example: libc.so → standard C library, required for almost all programs.

/boot → Boot Files

Purpose: Stores kernel and bootloader files needed to start the system.

Examples:

vmlinuz → Linux kernel

initrd.img → initial RAM disk

grub/ → bootloader files

