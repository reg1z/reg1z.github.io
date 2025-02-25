# 14 Passwords and Shadow Hashes

<iframe src="https://www.youtube.com/embed/P-BJP9wVH_U?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Changing User Passwords**
    - `passwd` allows users to **change their own password**.
    - Running `sudo passwd <username>` allows **changing another user's password**.
    - Some systems **enforce password complexity**, rejecting weak passwords.
- **Understanding the `/etc/passwd` File**
    - `/etc/passwd` contains **user account details** but **not passwords**.
    - Lists **usernames, home directories, and shell programs**.
    - Each entry includes **colon-separated fields** for user metadata.
- **Storing Password Hashes in `/etc/shadow`**
    - `/etc/shadow` holds **hashed passwords**, not plain text.
    - Only **root users** can view the shadow file (`sudo cat /etc/shadow`).
    - Passwords are stored as **hashed values** with added "salt" for security.
- **How Password Hashing Works**
    - Linux **hashes passwords** before storing them in `/etc/shadow`.
    - Hashing ensures **passwords aren’t stored as plain text**.
    - Login attempts **rehash input** and compare it to stored values.
- **Using Python to Generate Hashes**
    - Python’s `crypt` module can **simulate password hashing**.
    - Running `crypt.crypt("password", "$6$salt")` generates a **hashed password**.
    - Changing **one character** in input **completely alters** the hash output.
- **Security Implications of Stolen Hashes**
    - Hackers attempt **brute force or dictionary attacks** to crack hashes.
    - Adding **salt** makes it harder to use precomputed attack tables.
    - `sudo chage -l <username>` checks password expiration policies.


---
Next in Playlist: [15 Less, Grep, and Pipe](15%20Less,%20Grep,%20and%20Pipe.md)