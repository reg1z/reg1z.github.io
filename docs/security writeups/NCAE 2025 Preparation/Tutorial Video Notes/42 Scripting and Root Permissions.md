# 42 Scripting and Root Permissions

<iframe src="https://www.youtube.com/embed/48QKX_zhdno?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

What if you want to create a script that outputs a file(s) with particular ownership / permissions?
- owned by root?
- owned by another user / group?

When using a redirect operator, it essentially spawns a sub-shell in the background to do the writing of the information (output). This sub-sell will have the permissions of who you're logged in as - NOT the permissions used when executing the command itself. In other words, `sudo` won't allow you to redirect output to a file with root-only write permissions. `sudo` only applies to the initial command it prefixes, and not the write process(es) spawned by the redirect operators.

HOWEVER... If you script out the corresponding command and then execute that script as root, it will work correctly.
## Commands

### `tee`
Can write data to files. Good alternative to redirect operators when permissions are an issue

`echo sandbox | sudo tee file.txt`

---
Next in Playlist: [43 Scripted IP Changer Low Sophistication](43%20Scripted%20IP%20Changer%20Low%20Sophistication.md)