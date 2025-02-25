# 12 Exploring Sudoers and Removing Users

<iframe src="https://www.youtube.com/embed/7IsIjTBK7kk?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>
https://www.youtube.com/watch?v=7IsIjTBK7kk&list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M&index=12

- **Exploring the Sudoers File**
    - The sudoers file (`/etc/sudoers`) controls which users can execute commands with `sudo`.
    - Only the **root user** can read or modify this file.
    - `ls -l /etc/sudoers` shows **ownership and permission settings**.
- **Safely Editing the Sudoers File**
    - `visudo` is the recommended way to edit sudoers to prevent syntax errors.
    - Directly editing with `nano` or `vi` can break the system if mistakes are made.
    - Adding a user manually follows the format: `<username> ALL=(ALL) ALL`.
- **Granting Sudo Privileges**
    - Users can be added to the **sudo or admin group** to gain privileges.
    - `sudo usermod -aG sudo <username>` adds a user to the sudo group.
    - `sudo cat /etc/sudoers` verifies changes after applying them.
- **Removing a User from Sudoers**
    - The `visudo` command allows **removing a user’s sudo privileges**.
    - Deleting the user’s entry in `/etc/sudoers` removes access.
- **Deleting a User**
    - `sudo userdel <username>` removes a user account.
    - `sudo userdel -r <username>` deletes the user **and their home directory**.
    - If a deleted user owned files, Linux assigns them to a **numerical user ID**.


---
Next in Playlist: [13 Groups](13%20Groups.md)