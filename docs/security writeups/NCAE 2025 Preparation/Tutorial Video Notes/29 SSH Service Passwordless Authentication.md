# 29 SSH Service Passwordless Authentication

<iframe src="https://www.youtube.com/embed/MBmWgXb73gE?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Setting Up SSH Passwordless Authentication**
    - SSH allows **logging into a remote system without a password** using public-private key pairs.
    - Passwordless authentication improves **security and automation** by eliminating password entry.
    - SSH keys must be generated and placed in the correct locations for authentication.
- **Creating a New User for Testing**
    - `sudo adduser bob` creates a new user named **Bob** with a home directory.
    - A password is required initially but will not be needed after key-based authentication is set up.
    - SSH login as Bob requires using `ssh bob@<server_ip>` and entering Bob’s password.
- **Generating SSH Key Pairs**
    - Running `ssh-keygen -t ecdsa -f ~/id_bob_key` generates an **ECDSA key pair** for authentication.
    - The key pair includes a **private key** (`id_bob_key`) and a **public key** (`id_bob_key.pub`).
    - Passphrases are optional but add an extra **layer of security** to the private key.
- **Setting Up the `.ssh` Directory for Bob**
    - SSH keys must be stored in the `.ssh` directory inside the user’s home folder.
    - `sudo mkdir -p /home/bob/.ssh` creates the directory with proper structure.
    - Running `ls -a /home/bob/` confirms whether `.ssh` exists for Bob.
- **Adding the Public Key to Authorized Keys**
    - `sudo cp id_bob_key.pub /home/bob/.ssh/authorized_keys` saves Bob’s public key.
    - The `authorized_keys` file allows SSH access **without a password** for matching private keys.
    - Ownership must be correct: `sudo chown bob:bob /home/bob/.ssh/authorized_keys`.
- **Setting Correct Permissions for SSH Authentication**
    - SSH requires **strict permissions** for key-based authentication to work.
    - `chmod 700 /home/bob/.ssh` ensures only Bob can access the `.ssh` directory.
    - `chmod 644 /home/bob/.ssh/authorized_keys` grants read access only to Bob.
- **Testing SSH Passwordless Login**
    - Running `ssh -i ~/id_bob_key bob@<server_ip>` attempts authentication using the key.
    - If configured correctly, SSH should **log in without prompting for a password**.
    - Incorrect permissions or ownership **cause authentication failures**.
- **Using SCP to Transfer the Private Key**
    - `scp ~/id_bob_key sandbox@<server_ip>:/home/sandbox/` securely transfers the private key.
    - `sudo chown sandbox:sandbox /home/sandbox/id_bob_key` ensures correct ownership.
    - Proper permissions (`chmod 600 id_bob_key`) prevent SSH from **rejecting the key**.
- **Using `ssh-copy-id` for Simplified Setup**
    - The command `ssh-copy-id -i ~/id_bob_key.pub bob@<server_ip>` automates key installation.
    - This method **copies and configures** the public key in the `authorized_keys` file.
    - It ensures correct ownership and permissions, reducing manual setup errors.
- **Security Implications of Key-Based Authentication**
    - Keys eliminate **brute-force attacks on SSH passwords**.
    - If a private key is compromised, an attacker **gains full access** to the account.
    - Regularly rotating SSH keys and securing private keys is **essential for system security**.

---

Next in Playlist: [30 SSH Service Through The Router](30%20SSH%20Service%20Through%20The%20Router.md)