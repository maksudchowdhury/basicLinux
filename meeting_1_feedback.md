
1. **Inside vim editor in the Linux command line, how to search for a text?**
   - To search for a text in `vim`, press `/` followed by the text you want to search for and then press `Enter`. For example, to search for the word "example":
     ```vim
     /example
     ```

2. **What's the default permission when a new file is created? Answer in the numeric value.**
   - The default permission for a new file is `644` (rw-r--r--).

3. **User lock status in a Linux system.**
   - To check if a user account is locked, you can use the `passwd` command with the `-S` option:
     ```bash
     passwd -S username
     ```
     **Sample Output:**
     ```bash
     username L (Password locked)
     ```

4. **How to assign a different root folder for a new user than the default one.**
   - You can specify a different home directory when creating a new user with the `useradd` command using the `-d` option:
     ```bash
     sudo useradd -d /path/to/new/home username
     ```

5. **What's the default expiration time for a newly created user in Linux?**
   - By default, a newly created user does not have an expiration date set. You can check this with the `chage` command:
     ```bash
     sudo chage -l username
     ```
     **Sample Output:**
     ```bash
     Account expires: never
     ```

6. **What is sticky bit?**
   - The sticky bit is a permission bit that can be set on directories to restrict file deletion. When set, only the file owner, the directory owner, or the root user can delete or rename the files within that directory. To set the sticky bit:
     ```bash
     chmod +t /path/to/directory
     ```

7. **LVM types and its usage.**
   - LVM (Logical Volume Manager) types include:
     - **Physical Volumes (PV):** Physical storage devices.
     - **Volume Groups (VG):** Groups of physical volumes.
     - **Logical Volumes (LV):** Volumes created from volume groups.
   - Usage: LVM allows for flexible disk management, including resizing volumes, creating snapshots, and combining multiple physical disks into a single logical volume.

8. **Swap partition's definition and its work.**
   - A swap partition is a dedicated area on a disk used to extend the virtual memory of the system. When the physical RAM is full, inactive pages are moved to the swap space to free up RAM for active processes.

9. **If `fstab` is mistakenly edited, how to recover the system to boot properly?**
   - Boot into a live CD or rescue mode, mount the root filesystem, and correct the `fstab` file:
     ```bash
     sudo mount /dev/sdXn /mnt
     sudo nano /mnt/etc/fstab
     ```
     Replace `/dev/sdXn` with the appropriate device identifier.

10. **Why don't we use `mount -l`?**
    - The `-l` option in `mount` is not a standard option. Instead, use `mount` without options to list mounted filesystems:
      ```bash
      mount
      ```

11. **What's the minimum space requirement of boot partition and swap partition?**
    - **Boot partition:** Typically, 500MB to 1GB.
    - **Swap partition:** Generally, 1.5 to 2 times the size of the physical RAM.

12. **Tell me more about the other filesystems than xfs, ext4 in details.**
    - **Btrfs:** A modern filesystem with advanced features like snapshots, subvolumes, and built-in RAID support.
    - **ZFS:** Known for its robustness, data integrity, and scalability. It includes features like snapshots, cloning, and built-in compression.
    - **ReiserFS:** Known for its efficient handling of small files and journaling capabilities.
    - **F2FS:** Designed for NAND flash memory-based storage devices, providing better performance and lifespan.

13. **What will happen if we run the command `lvextend -L +10G` with the symbol `+`?**
    - The `+` symbol indicates that 10GB will be added to the existing size of the logical volume. For example, if the current size is 20GB, the new size will be 30GB.

14. **Tabular comparison between `lvs` and `lvdisplay`:**

    | Command    | Description                                      | Output Format       |
    |------------|--------------------------------------------------|---------------------|
    | `lvs`      | Displays information about logical volumes       | Tabular             |
    | `lvdisplay`| Displays detailed information about logical volumes | Detailed (verbose)  |

    **Example:**

    ```bash
    lvs
    ```

    **Sample Output:**

    ```bash
    LV     VG   Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
    root   vg0  -wi-ao---- <50.00g                                                    
    swap   vg0  -wi-ao----  10.00g                                                    
    ```

    ```bash
    lvdisplay
    ```

    **Sample Output:**

    ```bash
    --- Logical volume ---
    LV Path                /dev/vg0/root
    LV Name                root
    VG Name                vg0
    LV UUID                abcdefg-hijklmn-opqrst-uvwxyz
    LV Write Access        read/write
    LV Creation host, time hostname, 2025-02-09 10:00:00 +0000
    LV Status              available
    # open                 1
    LV Size                <50.00 GiB
    Current LE             12800
    Segments               1
    Allocation             inherit
    Read ahead sectors     auto
    - currently set to     256
    Block device           253:0
    ```
