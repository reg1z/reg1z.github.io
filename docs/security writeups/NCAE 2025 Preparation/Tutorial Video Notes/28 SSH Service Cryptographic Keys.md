# 28 SSH Service Cryptographic Keys

<iframe src="https://www.youtube.com/embed/GivTVjSUjRM?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Understanding SSH Cryptographic Keys**
    - SSH uses **asymmetric encryption** to ensure secure communication between clients and servers.
    - Encryption relies on **key pairs**—a **private key** (kept secret) and a **public key** (shared).
	- Any data encrypted with **one key** can only be decrypted with the **other key**.
- **Locating SSH Host Keys on a Server**
    - SSH host keys are stored in `/etc/ssh/` and labeled according to their encryption algorithm (`rsa`, `ecdsa`, `ed25519`).
    - The **private key (`ssh_host_algorithm_key`)** is confidential and must not be exposed.
    - The **public key (`ssh_host_algorithm_key.pub`)** is shared with clients when they connect.
- **How SSH Key Exchange Works**
    - When a client connects, the server **sends its public key** for authentication.
    - The client encrypts a message with this key, which only the **server’s private key** can decrypt.
    - This ensures **secure and verified communication**.
- **Different Encryption Algorithms Used in SSH**
    - SSH supports multiple key algorithms, including **RSA, ECDSA, and ED25519**.
    - Some algorithms are **more secure** than others due to key length and encryption strength.
    - The **NSA provides recommendations** on key lengths and preferred algorithms.
- **Viewing and Managing SSH Keys**
    - Running `ls -l /etc/ssh/` displays **key files and their permissions**.
    - Private keys are restricted to **root access only**, ensuring security.
    - Attempting to view a private key as a non-root user results in **permission denied**.
- **Understanding Known Hosts on Clients**
    - The first time a client connects to a server, its **public key is saved** in `~/.ssh/known_hosts`.
    - SSH warns users if a server’s key **changes unexpectedly**, preventing **man-in-the-middle attacks**.
    - Running `cat ~/.ssh/known_hosts` displays stored **server fingerprints**.
- **Generating New SSH Keys for a Server**
    - Cloned virtual machines **share identical SSH keys**, posing a **security risk**.
    - Running `sudo ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key` generates a **new ECDSA key**.
    - Generating new keys ensures that **each server has a unique identity**.
- **Handling Host Key Verification Errors**
    - If a server’s key changes, clients receive a **REMOTE HOST IDENTIFICATION HAS CHANGED!** warning.
    - Removing outdated keys from `~/.ssh/known_hosts` allows reconnection (`rm ~/.ssh/known_hosts`).
    - Reconnecting prompts users to **verify and accept the new fingerprint**.
- **Ensuring Secure SSH Key Management**
    - Private keys should **never be shared or exposed**, as they provide **server access**.
    - Proper key management ensures **clients can verify legitimate servers**.
    - Regularly updating and rotating keys enhances **long-term security**.


---
Next in Playlist: [29 SSH Service Passwordless Authentication](29%20SSH%20Service%20Passwordless%20Authentication.md)