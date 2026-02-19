Process Management 

ps aux – Show all running processes with details (PID, CPU, memory).
top – Real-time view of system processes and resource usage.
htop – Improved interactive process viewer (if installed).
kill <PID> – Send a signal (default: SIGTERM) to stop a process.
kill -9 <PID> – Force kill a process (SIGKILL).
nice -n 10 <cmd> – Start a command with lower CPU priority.
jobs – List background jobs in the current shell session.

File System 

ls -lh – List files with human-readable sizes.
cd <dir> – Change directory.
pwd – Show current working directory.
df -h – Show disk space usage of mounted filesystems.
du -sh <dir> – Show total size of a directory.
find /path -name file – Search for files by name.
chmod 755 file – Change file permissions.

Networking & Troubleshooting 

ip a – Show IP addresses and network interfaces.
ping google.com – Test connectivity to a host.
ss -tulnp – Show listening ports and associated processes.
curl http://example.com – Test HTTP connectivity to a URL.
traceroute google.com – Show path packets take to a host.
journalctl -xe – View detailed system logs (useful for service/network issues).
