# 07 Creating and Reading Files
![](https://www.youtube.com/watch?v=2DcDQe8idtU&list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M&index=7)

- **Creating Files with `touch`**  
	- `touch <filename>` creates an empty file.  
	- Can create multiple files at once by listing filenames.  
	- Updates timestamps if the file already exists.  
- **Writing to Files with `echo` and `>`**  
	- `echo "text" > file.txt` writes text to a file.  
	- Overwrites existing content unless `>>` is used to append.  
- **Viewing File Contents**  
	- `cat <filename>` displays the full file content.  
	- `less <filename>` allows **scrolling through content** interactively.  
	- `head <filename>` and `tail <filename>` show the **first or last lines** of a file.  
- **Editing Files with `nano`**  
	- `nano <filename>` opens a simple text editor in the terminal.  
	- Use `Ctrl + X` to exit, `Y` to save changes, and `N` to discard.  
- **Reading and Searching Inside Files**  
	- `grep "word" <filename>` finds lines containing a specific word.  
	- `grep -i "word" <filename>` makes the search **case-insensitive**.  
	- `grep -r "word" <directory>` searches recursively in a directory.  


---
Next in Playlist: [08 Editing with Nano or Vi](08%20Editing%20with%20Nano%20or%20Vi.md)