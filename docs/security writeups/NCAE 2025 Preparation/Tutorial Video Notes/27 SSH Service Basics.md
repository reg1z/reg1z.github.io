# 27 SSH Service Basics

<iframe src="https://www.youtube.com/embed/krqJhN4Ld6s?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Setting Up SSH on Ubuntu**
    - The Ubuntu machine will function as an **SSH server** alongside its web server role.
    - SSH is a key tool for **secure remote access** in cybersecurity and networking.
    - Before setup, check if the SSH service is already running using `systemctl status ssh`.
- **Verifying SSH Service Installation**
    - Ubuntu uses **`ssh` or `sshd`** for Secure Shell services.
    - Running `systemctl status sshd` confirms if the service is installed and active.
    - The default installation includes the **BSD Secure Shell Server**, often pre-installed.
- **Exploring SSH Configuration Files**
    - SSH configurations are located in `/etc/ssh/`.
    - Running `ls /etc/ssh/` reveals files like `sshd_config`, `ssh_config`, and key files (`.pub`).
    - The `sshd_config` file is critical for **server settings**, while `ssh_config` is for client settings.
- **Understanding the `sshd_config` File**
    - `nano /etc/ssh/sshd_config` opens the SSH server configuration file.
    - The file includes **default settings**, many of which are commented out but still active.
    - Important settings include `Port 22` (default SSH port) and `ListenAddress`.
- **Adjusting SSH Security Settings**
    - The `PermitRootLogin` setting controls **whether root can log in via SSH**.
    - `PermitRootLogin no` prevents root access, enhancing security.
    - The `ListenAddress` option can limit SSH access to specific IPs (`0.0.0.0` allows any IP).
- **Restarting SSH After Configuration Changes**
    - Changes to `sshd_config` require a service restart: `systemctl restart ssh`.
    - Running `systemctl status ssh` verifies if the changes were applied correctly.
    - Misconfigurations can cause SSH access issues, requiring **local troubleshooting**.
- **Testing SSH Connectivity**
    - The **internal Kali machine** is used to connect to the SSH server.
    - Running `ssh sandbox@192.168.<team_number>.2` attempts a secure connection.
    - The first connection prompts for **fingerprint verification** (`yes` to accept).
- **Logging into the Remote Server via SSH**
    - After accepting the fingerprint, SSH prompts for the **user’s password**.
    - A successful login grants access to the **Ubuntu system remotely**.
    - The prompt changes, indicating that commands now run on the **remote server**.
- **Running Commands on the Remote System**
    - Running `pwd` confirms the remote session directory (`/home/sandbox`).
    - `ip a` shows the remote machine’s IP configuration.
    - Remote users can edit files (`nano /etc/netplan/...`) or execute system commands.
- **Closing the SSH Session**
    - The `exit` command logs out of the SSH session, returning to the local machine.
    - Understanding SSH setup and configuration enables **secure remote administration**.


---

Next in Playlist: [28 SSH Service Cryptographic Keys](28%20SSH%20Service%20Cryptographic%20Keys.md)