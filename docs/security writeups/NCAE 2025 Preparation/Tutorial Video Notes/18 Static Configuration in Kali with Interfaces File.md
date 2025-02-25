# 18 Static Configuration in Kali with Interfaces File

<iframe src="https://www.youtube.com/embed/6AG68GIMw5o?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Understanding Static IP Configuration**
    - Linux assigns IP addresses dynamically unless configured manually.
    - Knowing how to set a **static IP** is critical for **network stability**.
    - Different **Linux distributions** use different configuration methods.
- **Finding Network Configuration Files**
    - Kali Linux stores network settings in `/etc/network/interfaces`.
    - Ubuntu and CentOS may use **different paths and tools**.
    - Modifying the wrong file can **break network connectivity**.
- **Editing the Interfaces File**
    - `sudo nano /etc/network/interfaces` opens the network settings.
    - **Ensure the correct file** is modified (`interfaces`, not `interface`).
    - The file defines **loopback (`lo`) and Ethernet (`eth0`) interfaces**.
- **Setting a Static IP Address**
    - Use `auto eth0` to **enable the interface on boot**.
    - Define `iface eth0 inet static` to set a **manual IP address**.
    - Configure `address`, `netmask`, and **gateway** based on the network topology.
- **Applying Network Changes**
    - Restart networking with `sudo systemctl restart networking`.
    - `ip a` verifies if the **new IP address is applied**.
    - Incorrect configurations can **disconnect the system** from the network.
- **Importance of Network Topology**
    - Some networks require **specific IP addresses** to function.
    - Dynamic (DHCP) vs. Static IPs depend on **network infrastructure**.
	- Configurations must **match the expected settings** to maintain connectivity.


---
Next in Playlist: [19 Static Configuration in CentOS with ifcfg Files](19%20Static%20Configuration%20in%20CentOS%20with%20ifcfg%20Files.md)