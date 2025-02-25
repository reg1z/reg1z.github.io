# 25 Router Configuration and Mini Hack Completion
> [!warning]+
> ==⚠️ 💥 ⚠️ NOTE: You will not be using a CentOS router in the 2025 NCAE challenge!!!⚠️ 💥 ⚠️==
> 
> ==⚠️ 💥 ⚠At this point it is recommended you skip this video and do the current year's Mini Hack before continuing with the rest of the playlist!!!⚠️ 💥 ⚠==
> 
> **⭐ Mini Hack 2025: [44 MicroTik Routers and Mini Hack 2025](44%20MicroTik%20Routers%20and%20Mini%20Hack%202025.md) ⭐**

<iframe src="https://www.youtube.com/embed/nm680gA5dXQ?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Configuring the Router in Mini Hack**
    - The router is set up using **CentOS** with two network interfaces.
    - Interfaces: `eth0` for the **external network (172.20.x.x)** and `eth1` for the **internal network (192.168.x.x)**.
    - Initial setup involves **configuring IP addresses** but does not include routing yet.
- **Understanding Firewall Zones in CentOS**
    - Firewall zones determine **network access rules**.
    - `firewall-cmd --list-all-zones` shows available zones like **public, external, and internal**.
    - By default, interfaces (`eth0` and `eth1`) are assigned to the **public zone**.
- **Checking and Changing Firewall Zones**
    - The firewall zones **govern network permissions** for each interface.
    - The **external zone** is preferred for `eth0`, while the **internal zone** is for `eth1`.
    - Changing zones is done via: `firewall-cmd --change-interface=eth0 --zone=external --permanent`.
- **Restarting and Verifying Firewall Settings**
    - Changes to the firewall require a **reload** using `firewall-cmd --reload`.
    - `firewall-cmd --list-all --zone=external` verifies **interface assignment and enabled services**.
- **Enabling Masquerading for Routing**
    - Masquerading allows **internal devices to use the router for external access**.
    - The external zone **has masquerading enabled by default**, reducing manual setup.
    - This enables internal machines to communicate with **external networks via the router**.
- **Configuring Port Forwarding for Web Traffic**
    - External web requests to `port 80` must be forwarded to the **internal web server**.
    - The command for forwarding:  
        `firewall-cmd --zone=external --add-forward-port=port=80:proto=tcp:toport=80:toaddr=192.168.x.x --permanent`
    - A firewall reload is required to apply the change.
- **Ensuring Gateway Configuration for Internal Devices**
    - Internal devices must have the router’s internal IP (`192.168.x.1`) **set as their default gateway**.
    - In Ubuntu, Netplan configuration is updated with `gateway4: 192.168.x.1`.
    - Restarting networking services applies the gateway settings.
- **Testing Network and Web Access**
    - `ping` tests internal devices' connectivity to the **router and external network**.
    - `curl` or a browser verifies if external traffic **reaches the internal web server**.
    - The **scoreboard system confirms** if the router and web services are properly configured.
- **Finalizing Mini Hack Setup**
    - A fully functional router allows internal devices to access external networks.
    - Port forwarding ensures **external web access is properly redirected**.
    - Understanding **firewall zones, masquerading, and gateways** is key to successful routing.


---
Next in Playlist: [26 Mini Hack Reconfiguration](26%20Mini%20Hack%20Reconfiguration.md)