# 34 Rsync Service Basics

<iframe src="https://www.youtube.com/embed/sF_hxz4lZk0?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Introduction to Rsync for Automation and Backups**
    - Rsync is a **powerful Linux utility** used for **file synchronization and backups**.
    - It is commonly used in **competition environments** to automate file management tasks.
    - The video demonstrates how Rsync can be used between **internal machines** in a Mini Hack setup.
- **Setting Up the Environment**
    - The demonstration uses **two internal machines**: an Ubuntu web server and a Kali system.
    - The Ubuntu machine is assigned `192.168.195.2`, and the Kali machine is `192.168.195.100`.
    - The machines must **communicate with each other** over the network for Rsync to function.
- **Creating Files for Rsync Testing**
    - A new directory named `stuff/` is created to store files for backup.
    - Two files (`practice1` and `practice2`) are created inside `stuff/` using the `touch` command.
    - A separate `backups/` directory is created to **store synced files**.
- **Basic Rsync Command Usage**
    - The command `rsync -av stuff/ backups/` synchronizes files between directories.
    - The `-a` (archive) option preserves **file permissions, timestamps, and symbolic links**.
    - The `-v` (verbose) option provides **detailed output** of the synchronization process.
- **Testing Rsync with Modified Files**
    - Adding new content to `practice1` using `echo "text" >> stuff/practice1` modifies the file.
    - Running `rsync -av stuff/ backups/` again updates **only the modified file**, not all files.
    - This efficiency is a key advantage over the `cp` command, which **copies all files blindly**.
- **Using Rsync with the `--delete` Option**
    - Running `rm stuff/practice2` removes `practice2` from the source directory.
    - By default, Rsync does **not delete missing files** from the backup directory.
    - Running `rsync -av --delete stuff/ backups/` ensures the **backup matches the source exactly**.
- **Weighing the Pros and Cons of `--delete`**
    - Using `--delete` ensures **full consistency** but risks losing accidentally deleted files.
    - Omitting `--delete` keeps old backups, leading to **excessive storage usage** over time.
    - A hybrid approach involves running **regular full backups** while keeping **incremental snapshots**.
- **Long-Term Backup Strategies**
    - Some organizations use **rolling backups** where Rsync **does not delete files immediately**.
    - Scheduled Rsync jobs (`cron`) automate backups on a **daily or weekly basis**.
    - Choosing the right backup strategy depends on **available storage and recovery needs**.
- **Final Thoughts on Rsync Usage**
    - Rsync is ideal for **fast, efficient, and incremental backups**.
    - The `-av` options provide **preservation and clarity**, while `--delete` ensures **synchronization**.
    - Understanding Rsync’s behavior helps **prevent data loss and optimize backup workflows**.

---
Next in Playlist: [35 Cron Service Intro](35%20Cron%20Service%20Intro.md)