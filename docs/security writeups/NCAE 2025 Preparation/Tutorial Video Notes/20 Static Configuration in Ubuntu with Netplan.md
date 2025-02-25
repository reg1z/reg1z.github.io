# 20 Static Configuration in Ubuntu with Netplan

<iframe src="https://www.youtube.com/embed/3vbFNmnJCl0?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Network Configuration in Ubuntu Using Netplan**
    - Ubuntu **no longer uses** `/etc/network/interfaces` for network configuration.
    - Instead, it relies on **Netplan**, with files stored in `/etc/netplan/`.
    - Netplan configurations are **YAML-based** and require precise indentation.
- **Finding and Editing Netplan Files**
    - `ls /etc/netplan/` lists available Netplan configuration files.
    - The default file is typically named `01-network-manager-all.yaml`.
    - Edit the file using `sudo nano /etc/netplan/<filename>.yaml`.
- **Setting a Static IP Address**
    - Under `ethernets:`, specify the network interface (e.g., `ens18`).
    - Define `addresses:` with the **desired IP address and subnet** (e.g., `192.168.118.2/24`).
    - Indentation is crucial; incorrect spacing **breaks the configuration**.
- **Applying Network Changes**
    - Use `sudo netplan apply` to apply the new configuration.
    - `ip a` verifies if the **new IP address is assigned**.
    - Syntax errors in the Netplan file can **prevent changes from taking effect**.
- **Differences from Other Linux Systems**
    - Ubuntu’s Netplan is different from Kali’s `/etc/network/interfaces`.
    - CentOS uses **`ifcfg-eth0` files** instead of Netplan.
	- Learning distribution-specific networking tools **improves troubleshooting skills**.


---
Next in Playlist: [21 Testing Connectivity with Ping](21%20Testing%20Connectivity%20with%20Ping.md)