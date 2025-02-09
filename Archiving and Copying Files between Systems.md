<h2 align=center> Archiving and Copying Files between Systems</h2>

### Managing Compressed tar Archives

The `tar` command is used to create, maintain, modify, and extract files that are archived in the tar format. It is often used in conjunction with compression utilities like `gzip` or `bzip2`.

#### Creating a Compressed tar Archive

To create a compressed tar archive, use the following command:

```bash
tar -czvf archive_name.tar.gz /path/to/directory
```

**Sample Output:**

```bash
tar: Removing leading `/' from member names
/path/to/directory/
/path/to/directory/file1
/path/to/directory/file2
```

#### Extracting a Compressed tar Archive

To extract a compressed tar archive, use the following command:

```bash
tar -xzvf archive_name.tar.gz
```

**Sample Output:**

```bash
/path/to/directory/
/path/to/directory/file1
/path/to/directory/file2
```

### Practice: Backing Up and Restoring Files From a tar Archive

#### Backing Up Files

To back up files into a tar archive, use the following command:

```bash
tar -cvf backup.tar /path/to/files
```

**Sample Output:**

```bash
/path/to/files/
/path/to/files/file1
/path/to/files/file2
```

#### Restoring Files

To restore files from a tar archive, use the following command:

```bash
tar -xvf backup.tar -C /path/to/restore
```

**Sample Output:**

```bash
/path/to/restore/
/path/to/restore/file1
/path/to/restore/file2
```

### Copying Files between Systems Securely

The `scp` (secure copy) command is used to copy files between hosts on a network securely.

#### Copying a File to a Remote System

To copy a file to a remote system, use the following command:

```bash
scp /path/to/local/file username@remote_host:/path/to/remote/directory
```

**Sample Output:**

```bash
file1 100%  123KB  1.2MB/s   00:00
```

#### Copying a File from a Remote System

To copy a file from a remote system, use the following command:

```bash
scp username@remote_host:/path/to/remote/file /path/to/local/directory
```

**Sample Output:**

```bash
file1 100%  123KB  1.2MB/s   00:00
```

### Practice: Copying Files over the Network with scp

#### Copying Multiple Files

To copy multiple files to a remote system, use the following command:

```bash
scp /path/to/local/file1 /path/to/local/file2 username@remote_host:/path/to/remote/directory
```

**Sample Output:**

```bash
file1 100%  123KB  1.2MB/s   00:00
file2 100%  456KB  1.5MB/s   00:00
```

### Synchronizing Files Between Systems Securely

The `rsync` command is used to synchronize files and directories between two locations over a network.

#### Synchronizing a Directory

To synchronize a directory to a remote system, use the following command:

```bash
rsync -avz /path/to/local/directory username@remote_host:/path/to/remote/directory
```

**Sample Output:**

```bash
sending incremental file list
./
file1
file2

sent 12345 bytes  received 6789 bytes  1234.56 bytes/sec
total size is 123456  speedup is 1.23
```

### Practice: Synchronizing Two Directories Securely with rsync

#### Synchronizing with Deletion

To synchronize a directory and delete files on the remote system that are not present on the local system, use the following command:

```bash
rsync -avz --delete /path/to/local/directory username@remote_host:/path/to/remote/directory
```

**Sample Output:**

```bash
sending incremental file list
deleting file3
./
file1
file2

sent 12345 bytes  received 6789 bytes  1234.56 bytes/sec
total size is 123456  speedup is 1.23
```

### Lab: Archiving and Copying Files between Systems

#### Step 1: Create a tar Archive

```bash
tar -cvf lab_backup.tar /path/to/lab/files
```

**Sample Output:**

```bash
/path/to/lab/files/
/path/to/lab/files/file1
/path/to/lab/files/file2
```

#### Step 2: Copy the tar Archive to a Remote System

```bash
scp lab_backup.tar username@remote_host:/path/to/remote/directory
```

**Sample Output:**

```bash
lab_backup.tar 100%  123KB  1.2MB/s   00:00
```

#### Step 3: Extract the tar Archive on the Remote System

```bash
ssh username@remote_host 'tar -xvf /path/to/remote/directory/lab_backup.tar -C /path/to/remote/restore'
```

**Sample Output:**

```bash
/path/to/remote/restore/
/path/to/remote/restore/file1
/path/to/remote/restore/file2
```
