# 35 Cron Service Intro

<iframe src="https://www.youtube.com/embed/Bc6ykGMooiY?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Introduction to Cron Service for Automation**
    - The **cron service** is a built-in Linux tool that allows administrators to **schedule and automate tasks**.
    - It is often used in cybersecurity for **automated backups, monitoring, and system maintenance**.
    - The goal is to integrate cron with `rsync` to create **scheduled backup processes**.
- **Checking if Cron Service is Running**
    - The cron service must be active for scheduled tasks to run.
    - Use `systemctl status cron` (Ubuntu) or `systemctl status crond` (CentOS) to check its status.
    - If it is not running, start it with `sudo systemctl start cron` and enable it with `sudo systemctl enable cron`.
- **Understanding Crontabs and Scheduled Jobs**
    - Cron jobs are managed using **crontabs**, which store **scheduled commands for execution**.
    - The command `crontab -e` opens the **user-specific crontab** for editing.
    - Each user has their **own crontab**, stored in `/var/spool/cron/crontabs/`.
- **Navigating the Crontab File**
    - When opening the crontab for the first time, users are prompted to **choose a text editor**.
    - The file contains **commented instructions**, but the real commands go at the bottom.
    - The crontab consists of **five time fields** followed by the command:
        - **Minute (0-59)**
        - **Hour (0-23)**
        - **Day of the month (1-31)**
        - **Month (1-12)**
        - **Day of the week (0-7, where both 0 and 7 represent Sunday)**
- **Creating a Basic Cron Job**
    - A simple cron job format: `0 5 * * 1 /path/to/script.sh`
    - This executes the script every **Monday at 5:00 AM**.
    - Wildcards (`*`) indicate **no restrictions** for that field (e.g., `* * * * *` runs every minute).
- **Testing a Cron Job with the `date` Command**
    - A quick way to verify cron is working is by logging the current time to a file.
    - Example: `* * * * * date >> /home/sandbox/Desktop/date_tracker.txt`
    - This runs the `date` command **every minute**, appending output to the `date_tracker.txt` file.
- **Locating User Crontabs on the System**
    - User-specific cron jobs are stored in `/var/spool/cron/crontabs/`, and require `sudo` to view.
    - Running `ls /var/spool/cron/crontabs/` shows which users have active crontabs.
    - Checking `sudo cat /var/spool/cron/crontabs/sandbox` reveals the scheduled tasks for that user.
- **Creating a Backup Automation with Rsync and Cron**
    - The `rsync` command can be scheduled to **automate file backups**.
    - Example cron job:
        
        ```
        * * * * * rsync -av /home/sandbox/Desktop/stuff/ /home/sandbox/Desktop/backups/  
        ```
        
    - This syncs the `stuff/` directory to `backups/` **every minute**, keeping files updated.
- **Avoiding Unwanted Deletions in Backups**
    - Using `--delete` in `rsync` removes **files that no longer exist in the source directory**.
    - For incremental backups, it’s best **not to use `--delete`** to preserve old files.
    - The decision depends on whether **consistency or retention of deleted files is preferred**.
- **Using System-Wide Cron Jobs**
    - The global cron file is stored in `/etc/crontab`.
    - Unlike user crontabs, `/etc/crontab` includes an **extra field for the user** executing the job.
    - Example:
        
        ```
        * * * * * root rsync -av /home/sandbox/Desktop/stuff/ /home/sandbox/Desktop/backups/  
        ```
        
    - This ensures the backup runs **even if no user is logged in**.
- **Monitoring and Securing Cron Jobs**
    - Cron jobs should be regularly reviewed to **prevent unauthorized tasks** from running.
    - Attackers may insert malicious cron jobs (e.g., **backdoor scripts**) that execute periodically.
    - Checking `/etc/crontab`, `/var/spool/cron/crontabs/`, and `/etc/cron.d/` helps identify **suspicious automation**.
- **Detecting Malicious Cron Entries**
    - Hackers may use cron to **re-establish a backdoor every minute**.
    - Example of a malicious cron job:
        
        ```
        * * * * * nc -l -p 12345 -e /bin/bash  
        ```
        
    - This creates a **persistent Netcat listener**, allowing remote shell access.
    - Security teams should **audit crontabs** to detect unauthorized changes.
- **Final Thoughts on Cron and Automation**
    - Cron is a **powerful tool** for scheduling system tasks, backups, and maintenance.
    - Understanding **user-specific vs. system-wide cron jobs** is essential for security.
    - Regular auditing ensures that **cron jobs are legitimate and not exploited by attackers**.


---
Next in Playlist: [36 Rsync and Cron Automatic Secure Backups](36%20Rsync%20and%20Cron%20Automatic%20Secure%20Backups.md)