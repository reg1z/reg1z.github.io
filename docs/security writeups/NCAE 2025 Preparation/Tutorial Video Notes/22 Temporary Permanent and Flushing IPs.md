# 22 Temporary Permanent and Flushing IPs

https://www.youtube.com/watch?v=von08e7PlWk&list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M&index=22

- **Adding Temporary IP Addresses**
    - `ip addr add <IP>/<subnet> dev <interface>` assigns a temporary IP.
    - Example: `sudo ip addr add 192.168.118.3/24 dev ens18`.
    - Temporary IPs **do not persist** after a reboot.
- **Checking and Managing Multiple IPs**
    - `ip a` lists all **assigned addresses** for an interface.
    - Multiple IPs can exist on **the same network adapter**.
    - `ifconfig` may not display all assigned addresses.
- **Flushing (Removing) All IP Addresses**
    - `ip addr flush dev <interface>` clears **all IP addresses** from an adapter.
    - Example: `sudo ip addr flush dev ens18`.
    - Useful for resetting configurations or troubleshooting network issues.
- **Restoring Permanent IP Configuration**
    - Temporary IPs do not modify **configuration files**.
    - `sudo netplan apply` restores saved Netplan settings.
    - Restarting the network service (`sudo systemctl restart networking`) also reloads permanent configurations.
- **Understanding When to Use Temporary vs. Permanent IPs**
    - Temporary IPs are useful for **testing or short-term changes**.
    - Permanent configurations ensure **reliable networking across reboots**.
    - Always update configuration files for **long-term network stability**.


---
Next in Playlist: [23 Using Networking Service with Netcat](23%20Using%20Networking%20Service%20with%20Netcat.md)