# 19 Static Configuration in CentOS with ifcfg Files

> [!warning]+ 
> ⚠️ 💥 ⚠️ **NOTE:** You will not be using a CentOS router in the 2025 NCAE challenge!!!⚠️ 💥 ⚠️
> 
> ==**You can safely skip this video!**==

<iframe src="https://www.youtube.com/embed/fQPJNI6zI8g?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>


- **Network Configuration in CentOS**
    - CentOS does **not use `/etc/network/interfaces`** like Debian-based systems.
    - Network configurations are managed in `/etc/sysconfig/network-scripts/`.
    - Each network interface has its own **`ifcfg-<interface>` file**.
- **Finding the Correct Interface File**
    - `ls /etc/sysconfig/network-scripts/` lists all network interface files.
    - Common interfaces include `ifcfg-eth0`, `ifcfg-eth1`, and `ifcfg-lo`.
    - Modifying the wrong file may result in **network misconfiguration**.
- **Editing Interface Configuration**
    - Open the correct file using `sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0`.
    - The file contains parameters like `BOOTPROTO`, `IPADDR`, and `NETMASK`.
    - `BOOTPROTO=dhcp` means **dynamic addressing**, while `static` requires manual setup.
- **Configuring a Static IP Address**
    - Set `BOOTPROTO=static` to manually assign an IP.
    - Add `IPADDR=<desired_IP>` and `NETMASK=<subnet_mask>` based on network topology.
    - `ONBOOT=yes` ensures the interface **activates on startup**.
- **Applying Network Changes**
    - Restart the network service with `sudo systemctl restart network`.
    - Use `ip a` to verify if the **new IP address was applied**.
    - Incorrect configurations may **disconnect the system from the network**.
- **Understanding Multi-Network Interfaces**
    - Servers can have **multiple network interfaces** (`eth0`, `eth1`).
    - Each interface may connect to **different networks**, requiring separate configurations.
    - Configuring both correctly allows **proper network routing** and communication.


---
Next in Playlist: [20 Static Configuration in Ubuntu with Netplan](20%20Static%20Configuration%20in%20Ubuntu%20with%20Netplan.md)