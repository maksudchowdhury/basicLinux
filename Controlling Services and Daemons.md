<h2 align=center>Controlling Services and Daemons in Linux</h2>

### Identifying Automatically Started System Processes

System processes that start automatically are typically managed by the `systemd` init system. To list all automatically started services, use the following command:

```bash
systemctl list-unit-files --type=service --state=enabled
```

**Sample Output:**

```bash
UNIT FILE                                  STATE   
accounts-daemon.service                    enabled 
acpid.service                              enabled 
apparmor.service                           enabled 
```

### Practice: Identify the Status of systemd Units

To check the status of a specific `systemd` unit, use the `systemctl status` command followed by the unit name. For example, to check the status of the `ssh` service:

```bash
systemctl status ssh
```

**Sample Output:**

```bash
● ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2025-02-09 10:00:00 UTC; 1h 23min ago
```

### Controlling System Service

You can start, stop, restart, and enable/disable services using the `systemctl` command.

#### Starting a Service

To start a service, use the following command:

```bash
systemctl start service_name
```

**Sample Output:**

```bash
(no output if successful)
```

#### Stopping a Service

To stop a service, use the following command:

```bash
systemctl stop service_name
```

**Sample Output:**

```bash
(no output if successful)
```

#### Restarting a Service

To restart a service, use the following command:

```bash
systemctl restart service_name
```

**Sample Output:**

```bash
(no output if successful)
```

#### Enabling a Service

To enable a service to start automatically at boot, use the following command:

```bash
systemctl enable service_name
```

**Sample Output:**

```bash
Created symlink /etc/systemd/system/multi-user.target.wants/service_name.service → /lib/systemd/system/service_name.service.
```

#### Disabling a Service

To disable a service from starting automatically at boot, use the following command:

```bash
systemctl disable service_name
```

**Sample Output:**

```bash
Removed /etc/systemd/system/multi-user.target.wants/service_name.service.
```

### Practice: Using systemctl to Manage Services

#### Checking the Status of a Service

To check the status of the `nginx` service, use the following command:

```bash
systemctl status nginx
```

**Sample Output:**

```bash
● nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2025-02-09 10:00:00 UTC; 1h 23min ago
```

#### Starting the nginx Service

To start the `nginx` service, use the following command:

```bash
systemctl start nginx
```

**Sample Output:**

```bash
(no output if successful)
```

#### Stopping the nginx Service

To stop the `nginx` service, use the following command:

```bash
systemctl stop nginx
```

**Sample Output:**

```bash
(no output if successful)
```

### Lab: Controlling Services and Daemons

#### Step 1: Identify Automatically Started Services

```bash
systemctl list-unit-files --type=service --state=enabled
```

**Sample Output:**

```bash
UNIT FILE                                  STATE   
accounts-daemon.service                    enabled 
acpid.service                              enabled 
apparmor.service                           enabled 
```

#### Step 2: Check the Status of a Service

```bash
systemctl status cron
```

**Sample Output:**

```bash
● cron.service - Regular background program processing daemon
   Loaded: loaded (/lib/systemd/system/cron.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2025-02-09 10:00:00 UTC; 1h 23min ago
```

#### Step 3: Start a Service

```bash
systemctl start cron
```

**Sample Output:**

```bash
(no output if successful)
```

#### Step 4: Stop a Service

```bash
systemctl stop cron
```

**Sample Output:**

```bash
(no output if successful)
```
