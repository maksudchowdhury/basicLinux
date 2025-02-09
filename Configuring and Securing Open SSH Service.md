<h2 align=center>Configuring and Securing Open SSH Service</h2>

### Accessing the Remote Command Line with SSH

The `ssh` command allows you to securely connect to a remote machine and access its command line.

#### Connecting to a Remote Machine

To connect to a remote machine, use the following command:

```bash
ssh username@remote_host
```

**Sample Output:**

```bash
username@remote_host's password:
Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-42-generic x86_64)
```

### Practice: Accessing the Remote Command Line

#### Connecting to a Remote Machine with a Specific Port

To connect to a remote machine using a specific port, use the following command:

```bash
ssh -p 2222 username@remote_host
```

**Sample Output:**

```bash
username@remote_host's password:
Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-42-generic x86_64)
```

### Configuring SSH Key-based Authentication

SSH key-based authentication provides a more secure way to connect to a remote machine without using a password.

#### Generating SSH Keys

To generate a pair of SSH keys, use the following command:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

**Sample Output:**

```bash
Generating public/private rsa key pair.
Enter file in which to save the key (/home/username/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/username/.ssh/id_rsa.
Your public key has been saved in /home/username/.ssh/id_rsa.pub.
````
#### Copying the Public Key to the Remote Machine

To copy the public key to the remote machine, use the following command:

```bash
ssh-copy-id username@remote_host
```

**Sample Output:**

```bash
username@remote_host's password:
Number of key(s) added: 1
Now try logging into the machine, with: "ssh 'username@remote_host'"
```

### Practice: Using SSH Key-based Authentication

#### Logging in with SSH Keys

To log in to a remote machine using SSH keys, use the following command:

```bash
sshremote_host
```

**Sample Output:**

```bash
Welcome to Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-42-generic x86_64)
```

### Customizing SSH Service Configuration

The SSH service configuration file is located at `/etc/ssh/sshd_config`. You can customize various settings to enhance security.

#### Editing the SSH Configuration File

To edit the SSH configuration file, use a text editor like `nano`:

```bash
sudo nano /etc/ssh/sshd_config
```

**Sample Output:**

```bash
# Example of overriding settings
# Port 22
# ListenAddress 0.0.0.0
# ListenAddress ::
```

#### Changing the Default SSH Port

To change the default SSH port, find the `Port` directive and set it to a different value:

```bash
Port 2222
```

#### Disabling Root Login

To disable root login, find the `PermitRootLogin` directive and set it to `no`:

```bash
PermitRootLogin no
```

#### Restarting the SSH Service

After making changes to the SSH configuration file, restart the SSH service:

```bash
sudo systemctl restart ssh
```

**Sample Output:**

```bash
(no output if successful)
```

### Practice: Restricting SSH Logins

#### Allowing Only Specific Users

To allow only specific users to log in via SSH, add the following directive to the SSH configuration file:

```bash
AllowUsers username1 username2
```

#### Restarting the SSH Service

After making changes, restart the SSH service:

```bash
sudo systemctl restart ssh
```

**Sample Output:**

```bash
(no output if successful)
```

### Lab: Configuring and Securing Open SSH Service

#### Step 1: Generate SSH Keys

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

**Sample Output:**

```bash
Generating public/private rsa key pair.
Enter file in which to save the key (/home/username/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/username/.ssh/id_rsa.
Your public key has been saved in /home/username/.ssh/id_rsa.pub.
```

#### Machine

```bash
ssh-copy-id username@remote_host
```

**Sample Output:**

```bash
username@remote_host's password:
Number of key(s) added: 1
Now try logging into the machine, with: "ssh 'username@remote_host'"
```

#### Step 3: Edit the SSH Configuration File

```bash
sudo nano /etc/ssh/sshd_config
```

**Sample Output:**

```bash
# Example of overriding settings
# Port 22
# ListenAddress 0.0.0.0
# ListenAddress ::
```

#### Step 4: Change the Default SSH Port

```bash
Port 2222
```

#### Step 5: Disable Root Login

```bash
PermitRootLogin no
```

#### Step 6: Restart the SSH Service

```bash
sudo systemctl restart ssh
```

**Sample Output:**

```bash
(no output if successful)
```
