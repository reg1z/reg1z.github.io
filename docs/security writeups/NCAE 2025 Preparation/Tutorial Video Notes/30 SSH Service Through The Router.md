# 30 SSH Service Through The Router

<iframe src="https://www.youtube.com/embed/NzitxTqu2o0?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Understanding SSH Access Through a Router**
    - The setup involves an **external Kali machine**, a **CentOS router**, and **internal systems**.
    - Internal devices communicate via SSH, but now **external access is needed**.
    - The router's **firewall configuration** determines whether SSH is accessible externally.
- **Checking Router Firewall Rules**
    - `firewall-cmd --list-all --zone=external` shows **allowed services and port forwards**.
    - The firewall allows **HTTP forwarding**, but SSH is also listed as a **permitted service**.
    - Many users mistakenly confuse **allowing a service** with **port forwarding**.
- **Verifying SSH Service on the Router**
    - The CentOS router has an **SSH server pre-installed and running**.
    - Checking with `systemctl status sshd` confirms that SSH is active.
    - The `/etc/ssh/` directory contains **configuration files and key pairs** for authentication.
- **Security Risks of Cloned SSH Keys**
    - If the router was cloned, its SSH keys **may be duplicated**, creating vulnerabilities.
    - Running `ls -a` reveals if SSH key files exist (`~/.ssh/authorized_keys`).
    - Unique keys should be generated for **each system** to prevent security risks.
- **Testing External SSH Access**
    - The external Kali machine attempts to SSH into the router at `172.20.x.1`.
    - SSH prompts the user to accept the **server's public key**, verifying authenticity.
    - After entering the password, the connection is established, confirming **external SSH access**.
- **Controlling SSH Access with Firewall Zones**
    - The router's **external zone** currently allows SSH connections.
    - This may not be desirable—administrators may **limit SSH to internal connections only**.
    - Checking `firewall-cmd --list-all --zone=internal` verifies if SSH is allowed **internally as well**.
- **Blocking SSH from External Connections**
    - To restrict SSH access to **internal connections only**, remove it from the external zone:  
        `firewall-cmd --zone=external --permanent --remove-service=ssh`
    - A firewall reload (`firewall-cmd --reload`) applies the changes.
    - External SSH attempts now **fail**, preventing unauthorized access.
- **Verifying Internal SSH Access**
    - The internal Kali machine attempts SSH to `192.168.x.1` (router’s internal IP).
    - SSH succeeds, confirming **internal access remains functional**.
    - This setup ensures **only trusted internal devices** can manage the router via SSH.
- **Re-Enabling External SSH if Needed**
    - If external troubleshooting is necessary, SSH can be **re-enabled** with:  
        `firewall-cmd --zone=external --permanent --add-service=ssh && firewall-cmd --reload`
    - Administrators must **carefully balance security vs. accessibility**.
- **Port Forwarding SSH to Internal Servers**
    - Instead of exposing the router’s SSH, external SSH can be forwarded to **an internal server**.
    - Using `firewall-cmd --add-forward-port=port=22:proto=tcp:toport=22:toaddr=192.168.x.2 --permanent`, SSH traffic redirects to the internal Ubuntu machine.
    - A firewall reload applies the new forwarding rule.
- **Testing the Port Forwarding Setup**
    - An external SSH attempt to the router now **redirects to the internal Ubuntu machine**.
    - The system warns of a **host key mismatch** because it connects to a different system.
    - Removing the old known host entry (`rm ~/.ssh/known_hosts`) allows SSH to proceed.
- **Understanding the Difference Between Services and Port Forwarding**
    - **Allowing SSH as a service** lets users connect **directly to the router**.
    - **Port forwarding** routes SSH traffic **to an internal device** instead.
    - Administrators must decide **which setup is best** based on security needs.


---

Next in Playlist: [31 DNS Service Basics](31%20DNS%20Service%20Basics.md)