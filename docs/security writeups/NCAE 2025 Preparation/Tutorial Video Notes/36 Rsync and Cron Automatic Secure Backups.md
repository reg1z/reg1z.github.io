# 36 Rsync and Cron Automatic Secure Backups

<iframe src="https://www.youtube.com/embed/SrPBebFADDM?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Expanding Rsync for Secure Backups Across a Network**
    - The goal is to move beyond local Rsync backups and securely transfer data to another machine on the network.
    - A **Kali Linux machine** will act as a **backup server**, receiving files from an **Ubuntu web server**.
    - The process leverages **SSH for secure transmission**, similar to the SCP command.
- **Enabling SSH on the Backup Server (Kali)**
    - The SSH service must be running to allow remote access.
    - `systemctl status sshd` confirms whether the SSH service is active.
    - If inactive, start it with `sudo systemctl start ssh` and verify with `ssh sandbox@192.168.195.100`.
- **Creating a Backup Directory Structure**
    - A dedicated folder (`backups/`) is created on the **Kali machine** for organization.
    - `mkdir -p ~/backups/website/` allows separate **backup locations for different services**.
    - Keeping structured backups prevents **overwriting and confusion** when managing multiple systems.
- **Running Rsync with SSH for Secure Transfer**
    - Rsync’s `-e` option allows execution over SSH:
        
        ```
        rsync -av -e ssh ~/Desktop/stuff/ sandbox@192.168.195.100:~/backups/website/  
        ```
        
    - This command securely transfers the `stuff/` directory from the Ubuntu machine to Kali’s backup location.
    - Upon execution, Rsync prompts for the **user’s SSH password**, confirming secure authentication.
- **Handling SSH Prompts in Automated Scripts**
    - If Rsync is scheduled in a cron job, manual password entry becomes **problematic**.
    - Automating Rsync requires **passwordless SSH authentication** using **public-private key pairs**.
    - Avoiding **storing plaintext passwords in cron jobs** is critical for security.
- **Setting Up SSH Key-Based Authentication**
    - A new SSH key is generated using `ssh-keygen -t ecdsa -f ~/backup_keys`.
    - The **private key** remains on the Ubuntu system, while the **public key** is copied to Kali:
        
        ```
        scp ~/backup_keys.pub sandbox@192.168.195.100:~/.ssh/authorized_keys  
        ```
        
    - Now, Rsync can authenticate **without prompting for a password**.
- **Automating Rsync Backups Using Cron**
    - Cron is used to **schedule recurring Rsync tasks** at specified intervals.
    - The command `crontab -e` opens the **user’s cron job configuration**.
    - A new cron job is added to run Rsync **every hour**:
        
        ```
        0 * * * * rsync -av -e "ssh -i /root/backup_keys" ~/Desktop/stuff/ sandbox@192.168.195.100:~/backups/website/  
        ```
        
    - The `-i` flag ensures SSH uses the **correct private key for authentication**.
- **Verifying Automated Backups**
    - Checking the backup directory on the Kali machine (`ls ~/backups/website/`) confirms successful transfers.
    - If files **do not appear**, common debugging steps include:
        - Checking cron logs with `cat /var/log/syslog | grep CRON`.
        - Ensuring SSH keys have **correct permissions** (`chmod 600 ~/.ssh/backup_keys`).
        - Running Rsync manually to detect **authentication issues**.
- **Preventing Backup Compromise**
    - If the web server is hacked, attackers could potentially **delete backup files**.
    - Best practices include:
        - **Isolating the backup server** from external network access.
        - **Disabling SSH access** when not in use.
        - **Rotating backup keys** regularly to prevent unauthorized access.
- **Implementing Offline Backup Strategies**
    - A **disconnected backup system** prevents attacks from spreading.
    - The backup server can be manually **brought online for sync**, then immediately disconnected.
    - This method ensures backups **remain intact** even if the primary system is compromised.
- **Final Thoughts on Rsync and Secure Automation**
    - Rsync combined with SSH provides **a secure and efficient backup solution**.
    - Automating with cron ensures **regular backups without manual intervention**.
    - Proper security measures, including **SSH key management and offline backups**, help **protect critical data**.


---
Next in Playlist: [37 Intro to Firewalls with UFW](37%20Intro%20to%20Firewalls%20with%20UFW.md)