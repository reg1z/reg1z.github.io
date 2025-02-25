# 11 Managing Permissions and Sudo Users

<iframe src="https://www.youtube.com/embed/to0GrfGERK0?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Understanding File Permissions**
    - `ls -l` displays file **permissions**, owner, and group.
    - Permissions are divided into **owner, group, and others**.
    - `rwx` represents **read (r), write (w), and execute (x)** permissions.
- **Modifying File Permissions**
    - `chmod <permissions> <file>` changes file permissions.
    - Numeric mode: `chmod 777 <file>` grants **full access**.
    - Symbolic mode: `chmod u+w <file>` adds **write permission** for the owner.
- **Changing File Ownership**
    - `chown <user>:<group> <file>` assigns a new owner and group.
    - `sudo` is required to change ownership of files **not owned by the user**.
- **Understanding Sudo Privileges**
    - `sudo <command>` runs a command with **administrator privileges**.
    - Users must be **listed in the sudoers file** to execute `sudo`.
    - `visudo` is used to **edit the sudoers file** safely.
- **Managing Access Restrictions**
    - `chmod 700 <directory>` allows **only the owner** to access a folder.
    - Removing write permissions restricts users from **modifying files**.
    - Group and user permissions define **who can access and modify data**.


---
Next in Playlist: [12 Exploring Sudoers and Removing Users](12%20Exploring%20Sudoers%20and%20Removing%20Users.md)