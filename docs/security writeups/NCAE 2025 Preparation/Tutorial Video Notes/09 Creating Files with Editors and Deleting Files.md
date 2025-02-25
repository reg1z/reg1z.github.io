# 09 Creating Files with Editors and Deleting Files

<iframe src="https://www.youtube.com/embed/l0d7ks9ZkjU?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Creating Files with Text Editors**
    - Running `nano <filename>` or `vi <filename>` on a non-existent file **creates a new file**.
    - Nano displays a warning when creating a file, while Vi requires entering **Insert Mode (`i`)** before adding text.
    - Saving in Nano: `Ctrl + X`, `Y`, `Enter`.
    - Saving in Vi: `Esc`, `:wq`, `Enter`.
- **Avoiding Common Mistakes**
    - Accidentally opening a **directory** in Nano or Vi produces a warning.
    - Using `Tab` for **auto-completion** prevents typos and accidental new file creation.
- **Deleting Files with `rm`**
    - `rm <filename>` removes a file permanently.
    - Can delete **multiple files** at once by listing filenames.
    - Running `rm` on non-existent files returns an error.

---
Next in Playlist: [10 Creating User Accounts](10%20Creating%20User%20Accounts.md)
