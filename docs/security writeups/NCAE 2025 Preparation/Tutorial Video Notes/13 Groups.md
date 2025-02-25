# 13 Groups

<iframe src="https://www.youtube.com/embed/BJJBSUe5JEk?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Understanding User Groups**  
	- Every user belongs to at least **one group**, often named after the user.  
	- Groups help manage **permissions** for multiple users.  
	- `groups` command shows **all groups** a user belongs to.  
- **Checking Group Memberships**  
	- `groups <username>` lists a specific user’s groups.  
	- `id <username>` provides **numeric group IDs (GIDs)**.  
- **Managing User Groups**  
	- `sudo usermod -aG <group> <user>` adds a user to a group.  
	- `sudo gpasswd -d <user> <group>` removes a user from a group.  
	- Users must **log out and back in** for group changes to take effect.  
- **Viewing System Groups**  
	- `/etc/group` file lists **all groups and their members**.  
	- `cat /etc/group` displays the **group database**.  
- **Granting Sudo Access Through Groups**  
	- Users in the `sudo` group can execute **admin commands**.  
	- `sudo usermod -aG sudo <user>` grants **sudo privileges**.
	- Users must belong to a **group listed in `/etc/sudoers`** to run `sudo` commands.  


---
Next in Playlist: [14 Passwords and Shadow Hashes](14%20Passwords%20and%20Shadow%20Hashes.md)