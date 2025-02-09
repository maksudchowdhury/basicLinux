<h2 align=center>Analyzing and Storing Logs in Linux</h2>

### System Log Architecture

Linux uses a centralized logging system to record various system events. The primary components of this architecture include `syslog`, `rsyslog`, and `systemd-journald`.

#### Viewing the System Log Architecture

To view the system log architecture, you can check the configuration files and directories:

```bash
ls /etc/rsyslog.conf /etc/rsyslog.d/
```

**Sample Output:**

```bash
/etc/rsyslog.conf
/etc/rsyslog.d/
```

### Practice: System Logging Components

#### Checking the Status of rsyslog

To check the status of the `rsyslog` service, use the following command:

```bash
systemctl status rsyslog
```

**Sample Output:**

```bash
● rsyslog.service - System Logging Service
   Loaded: loaded (/lib/systemd/system/rsyslog.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2025-02-09 10:00:00 UTC; 1h 23min ago
```

### Reviewing Syslog Files

Syslog files are typically stored in the `/var/log` directory. Common log files include `syslog`, `auth.log`, and `kern.log`.

#### Viewing Syslog Files

To view the contents of the `syslog` file, use the following command:

```bash
cat /var/log/syslog
```

**Sample Output:**

```bash
Feb  9 10:00:00 hostname systemd[1]: Started Session 1 of user root.
Feb  9 10:00:01 hostname CRON[1234]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

### Practice: Finding Log Entries

#### Searching for Specific Log Entries

To search for specific log entries, use the `grep` command. For example, to find all entries related to `sshd`:

```bash
grep sshd /var/log/syslog
```

**Sample Output:**

```bash
Feb  9 10:00:00 hostname sshd[5678]: Server listening on 0.0.0.0 port 22.
Feb  9 10:00:00 hostname sshd[5678]: Server listening on :: port 22.
```

### Reviewing systemd Journal Entries

The `systemd-journald` service collects and stores logging data. You can use the `journalctl` command to view these logs.

#### Viewing Journal Entries

To view the journal entries, use the following command:

```bash
journalctl
```

**Sample Output:**

```bash
-- Logs begin at Sun 2025-02-09 10:00:00 UTC, end at Sun 2025-02-09 11:23:45 UTC. --
Feb 09 10:00:00 hostname systemd[1]: Started Session 1 of user root.
Feb 09 10:00:01 hostname CRON[1234]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

### Practice: Finding Events with Journalctl

#### Filtering Journal Entries by Service

To filter journal entries by a specific service, use the `-u` option. For example, to view entries for the `sshd` service:

```bash
journalctl -u sshd
```

**Sample Output:**

```bash
-- Logs begin at Sun 2025-02-09 10:00:00 UTC, end at Sun 2025-02-09 11:23:45 UTC. --
Feb 09 10:00:00 hostname sshd[5678]: Server listening on 0.0.0.0 port 22.
Feb 09 10:00:00 hostname sshd[5678]: Server listening on :: port 22.
```

### Preserving the systemd Journal

By default, `systemd-journald` stores logs in a volatile manner. To make the logs persistent, you need to configure the journal to store logs on disk.

#### Configuring Persistent Journals

To configure persistent journals, create the directory `/var/log/journal` and restart the `systemd-journald` service:

```bash
sudo mkdir -p /var/log/journal
sudo systemctl restart systemd-journald
```

**Sample Output:**

```bash
(no output if successful)
```

### Practice: Configure a Persistent systemd Journal

#### Verifying Persistent Journals

To verify that the journal is now persistent, check the storage setting:

```bash
sudo journalctl --disk-usage
```

**Sample Output:**

```bash
Archived and active journals take up 16.0M in the file system.
```

### Maintaining Accurate Time

Accurate system time is crucial for log timestamps and system operations. The `timedatectl` command is used to manage system time and date settings.

#### Checking the Current Time and Date

To check the current time and date, use the following command:

```bash
timedatectl
```

**Sample Output:**

```bash
               Local time: Sun 2025-02-09 11:23:45 UTC
           Universal time: Sun 2025-02-09 11:23:45 UTC
                 RTC time: Sun 2025-02-09 11:23:45
                Time zone: UTC (UTC, +0000)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
```

### Practice: Adjusting System Time

#### Setting the Time Zone

To set the system time zone, use the following command:

```bash
sudo timedatectl set-timezone Asia/Dhaka
```

**Sample Output:**

```bash
(no output if successful)
```

#### Synchronizing the System Clock with NTP

To synchronize the system clock with an NTP server, use the following command:

```bash
sudo timedatectl set-ntp true
```

**Sample Output:**

```bash
(no output if successful)
```
