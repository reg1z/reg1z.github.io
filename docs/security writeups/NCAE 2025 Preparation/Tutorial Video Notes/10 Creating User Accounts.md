# 10 Creating User Accounts

<iframe src="https://www.youtube.com/embed/y6-e233rrQE?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Checking Your Current User**
    - `whoami` displays the **current logged-in user**.
    - Important for **multi-user systems** to track identities.
- **Creating a New User**
    - `adduser <username>` creates a new user account.
    - Requires **root privileges**, so `sudo adduser <username>` is necessary.
    - Prompts for a **password** and optional personal details.
- **Understanding Home Directories**
    - New users get a home directory at `/home/<username>`.
    - Default settings may vary depending on the system.
- **Switching Users**
    - `su <username>` switches to another user.
    - Prompts for the **target user’s password**.
    - File paths may change depending on the user’s **home directory**.
- **User Permissions**
    - User access and security depend on **permissions**.
    - Some actions require **administrator privileges** (`sudo`).


---
Next in Playlist: [11 Managing Permissions and Sudo Users](11%20Managing%20Permissions%20and%20Sudo%20Users.md)