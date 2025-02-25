# 05 Moving and Copying

<iframe src="https://www.youtube.com/embed/gSVg40u0fZE?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Moving Files and Directories with `mv`**  
	- `mv` (Move) command performs a **cut and paste** in one step.  
	- Requires **two arguments**: the item to move and the destination.  
	- Supports **relative and absolute paths** for flexibility.  
	- Can move **multiple items** at once by listing multiple files before the destination.  
- **Checking Moved Items**  
	- `ls <directory>` can confirm a file’s new location without navigating into the directory.  
	- GUI can be used to visually verify the changes.  
- **Copying Files and Directories with `cp`**  
	- `cp` (Copy) creates a **duplicate** of a file or folder.  
	- Works like `mv` but leaves the original file untouched.  
	- Requires **two arguments**: the item to copy and the destination.  
	- To copy a **directory**, use `cp -r` (recursive copy), as `cp` alone only copies files.  
- **Using Options with Commands**  
	- Many commands support **options** like `-r` for recursive copying.  
	- Options **modify behavior** and are useful when handling directories.  
	- `Tab` completion helps avoid typos and speeds up command execution.  


---
Next in Playlist: [06 Removing Directories and Using the History](06%20Removing%20Directories%20and%20Using%20the%20History.md)