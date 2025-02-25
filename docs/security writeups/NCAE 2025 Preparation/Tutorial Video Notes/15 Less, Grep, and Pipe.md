# 15 Less, Grep, and Pipe

<iframe src="https://www.youtube.com/embed/2neT3phfYts?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Viewing Large Files with `less`**  
	- `less <filename>` opens a file for **scrolling through long outputs**.  
	- Arrow keys **navigate up and down**, `q` exits.  
	- Useful in **non-GUI environments** where scrolling is limited.  
- **Piping Output to `less`**  
	- `command | less` redirects command output to `less` for **easier reading**.  
	- Works with commands like `ls`, `cat`, and `grep`.  
	- Prevents **overflowing output** from scrolling off the screen.  
- **Using `grep` to Search in Files**  
	- `grep <word> <file>` finds lines containing a **specific term**.  
	- `grep sandbox /etc/group` filters for "sandbox" in the **group file**.  
	- `sudo grep sandbox /etc/shadow` searches **privileged files**.  
- **Piping Output to `grep`**  
	- `command | grep <word>` filters command output in **real-time**.  
	- Example: `cat /etc/passwd | grep sandbox` finds "sandbox" user details.  
	- Works with **any command generating text output**.  
- **Redirecting Output to a File**  
	- `command > file.txt` saves **output to a file**, overwriting existing content.  
	- `command >> file.txt` **appends output** instead of overwriting.  
	- Example: `grep sandbox /etc/group > sandbox_groups.txt` saves **filtered results**.  
- **Combining Commands for Efficiency**  
	- Commands can be **chained** using pipes (`|`) to **filter and process** data.  
	- Example: `ls /etc | grep conf | less` finds **config files** and scrolls through them.  
	- Efficient command usage **improves data management** and security.  


---
Next in Playlist: [16 Background on Services](16%20Background%20on%20Services.md)