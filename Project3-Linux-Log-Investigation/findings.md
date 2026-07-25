# Findings

## Observation 1
The `/var/log/auth.log` file stores authentication-related events such as user logins, SSH authentication, and sudo activity.

## Observation 2
The `/var/log/syslog` file stores general system events, service messages, and operating system logs.

## Observation 3
During this investigation, I found `sudo` and `authentication` entries inside `auth.log`, confirming that the log records authentication-related activity.

## Log Investigation Progress

### Authentication Log

 - Located the authentication log at ' /var/log/auth.log '.
 - Learned that 'auth.log' stores the authentication events.
 - Observed timestamps, usernames, and service names in log entries.
 - Identified 'systemd' as a Linux service that  records system events.
 - Learned that 'sudo' activity is logged, including the exact command executed.
 - Searched for SSH  ('sshd) entries.
 - No actual SSH login attempts were found in the current log. The only 'sshd' match was  the search command itself being logged.


## Journal Investigation

### Commands Used

journalctl -n 20

journalctl -n 50 | grep ssh

journalctl -n 100 | grep sudo

journalctl -n 200 | grep failed

### Findings

- Learned that `journalctl` reads logs from the systemd journal.
- Learned that `-n` displays the latest N journal entries.
- Learned to combine `journalctl` with `grep` for log filtering.
- Investigated SSH, sudo, and failed-event related logs.
- Understood that journal entries can be filtered without opening multiple log files.


## Kernel Investigation

### Commands Used

sudo dmesg | tail -20

sudo dmesg | grep -i usb

### Findings

- Learned that `dmesg` displays kernel messages.
- Learned that administrator privileges (`sudo`) are required to access kernel logs on this system.
- Observed VirtualBox USB Tablet device detection.
- Identified VirtualBox as the USB device manufacturer.
- Learned that kernel logs can help investigate hardware events such as USB device connections.


## Key Lessons Learned

- Authentication logs are investigated before system logs in many SOC investigations.
- Always investigate based on evidence instead of making assumptions.
- Different Linux tools serve different purposes:
- auth.log → Authentication
- syslog → General system events
  - journalctl → Systemd journal
  - dmesg → Kernel and hardware events
- Linux commands become much more powerful when combined using pipes (`|`) and `grep`.

## Final Reflection

This project improved my understanding of Linux log investigation from a SOC analyst's perspective. I learned how to identify authentication events, investigate system logs, analyze kernel messages, and support conclusions using evidence instead of assumptions.

