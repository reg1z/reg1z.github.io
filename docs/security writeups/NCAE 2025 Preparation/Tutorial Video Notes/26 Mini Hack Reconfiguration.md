# 26 Mini Hack Reconfiguration

> [!info]+ 
> ==**NOTE:** Video 26 is a recap of the original Mini Hack and you might consider skipping it, or watching it explicitly for the methodology presented.==

<iframe src="https://www.youtube.com/embed/AujsQji3A1Q?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Reconfiguring the Mini Hack Environment**
    - The Mini Hack is reset by **deleting the previous environment** and creating a new one.
    - The new environment assigns a **different team number**, requiring reconfiguration.
    - The goal is to **rebuild the network quickly**, focusing on efficiency.
- **Checking Scoreboard for Team Assignment**
    - `172.20.0.1` hosts the scoreboard, which tracks **assigned team numbers**.
    - Logging in with the sandbox user (`password`) reveals the **new team number**.
    - The scoreboard initially shows **all services as offline** until configured.
- **Configuring the Router**
    - The router has **no GUI** and requires manual configuration via the command line.
    - Logging in with `sandbox/password` grants access to CentOS configurations.
    - The **IP addresses must be assigned** for both external (`eth0`) and internal (`eth1`) interfaces.
- **Editing Network Configuration for Router**
    - The configuration file is located at `/etc/sysconfig/network-scripts/ifcfg-eth0`.
    - `eth0` (external) is set to `172.20.<team_number>.1/16`, while `eth1` (internal) is `192.168.<team_number>.1/24`.
    - Each interface is assigned to the correct **firewall zone** (`external` for `eth0`, `internal` for `eth1`).
    - Changes are applied using `systemctl restart network`.
- **Testing Router Connectivity**
    - `ip a` verifies if the **IP addresses were applied correctly**.
    - The scoreboard updates to indicate that the **router is online**.
    - The next step is configuring the **internal web server**.
- **Setting Up Port Forwarding for the Web Server**
    - Firewall settings must forward **port 80 traffic** from `eth0` to the web server at `192.168.<team_number>.2`.
    - The command: `firewall-cmd --zone=external --add-forward-port=port=80:proto=tcp:toport=80:toaddr=192.168.<team_number>.2 --permanent`.
    - `firewall-cmd --reload` applies changes, and `firewall-cmd --list-all --zone=external` verifies the configuration.
- **Configuring the Web Server (Ubuntu Machine)**
    - Ubuntu uses **Netplan** to configure static IPs, found at `/etc/netplan/01-network-manager-all.yaml`.
    - `ens18` is assigned `192.168.<team_number>.2/24`, with `192.168.<team_number>.1` as the gateway.
    - `sudo netplan apply` applies the new configuration, and `ip a` confirms the assigned IP.
- **Starting Apache Web Server**
    - `systemctl status apache2` checks if Apache is running.
    - `sudo systemctl start apache2` activates the service, allowing web content to be served.
    - Visiting `http://192.168.<team_number>.2` in a browser verifies that the server is online.
- **Updating Web Page Content for Scoring**
    - The scoreboard requires the website to display `Team <team_number>`.
    - `sudo nano /var/www/html/index.html` is used to update the **index file**.
    - After saving, refreshing the browser confirms the change, and the scoreboard reflects a **successful configuration**.
- **Finalizing Internal Kali Machine Configuration**
    - The internal Kali machine is configured with `192.168.<team_number>.100/24`.
    - The `/etc/network/interfaces` file is updated manually to set static addressing.
    - Restarting networking services (`systemctl restart networking`) applies the new settings.
    - A `ping` test confirms connectivity between **Kali, the router, and the web server**.

---

#### Next in Playlist: [27 SSH Service Basics](27%20SSH%20Service%20Basics.md)