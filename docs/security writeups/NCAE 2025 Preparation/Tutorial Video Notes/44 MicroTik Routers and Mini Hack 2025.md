# 44 MicroTik Routers and Mini Hack 2025
- hierarchical command structure
	- tab completion → list subcommands
	- important configuration categories
		- /ip
			- /ip address print
			- /ip route print
			- /ip service print → shows active services the router is running. These are reachable within the browser at different ports
				- Ask yourself, what are the other ways to access this device? What are the security implications of doing so?
			- 
		- /interface
	- tools
		- /ping
- Web interface - `http://172.20.46.1:8080`
	- During the NCAE competition, you will be provided with access to a default gateway/router that grants access to the external internet. This will need to be configured in the web interface.
	- There will also be external DNS servers
- Other things to know
	- winbox
	- services
		- telnet
		- ftp
		- www
		- ssh
		- www-ssl
		- api
		- winbox
		- api-ssl


# 44 MicroTik Routers and Mini Hack 2025

> [!info]+ 
> If you're here from [Video 25](25%20Router%20Configuration%20and%20Mini%20Hack%20Completion.md), you can head to where you'd normally continue after here: [26 Mini Hack Reconfiguration](26%20Mini%20Hack%20Reconfiguration.md)
> 
> ==**NOTE:** Video 26 is a recap of the original Mini Hack and you might consider skipping it, or watching explicitly it for the methodology presented.==

<iframe src="https://www.youtube.com/embed/gu5A2yCITRs?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Transitioning to MikroTik Routers for 2025 Mini Hack**
    - The competition is moving away from **CentOS-based routers** due to end-of-life support.
    - **MikroTik routers** will be used in the 2025 season for Mini Hack and competition environments.
    - Participants must familiarize themselves with **basic MikroTik commands and configurations**.
- **Deploying a Mini Hack with MikroTik**
    - The **Mini Hack environment** now includes a MikroTik router instead of CentOS.
    - Competitors can still deploy CentOS for practice, but MikroTik is the **primary competition router**.
    - The first step is **logging into the scoreboard** to check **assigned team numbers and router status**.
- **Accessing the MikroTik Router**
    - The router can be accessed via:
        - **NoVNC session (browser-based CLI)**.
        - **SSH (if configured)**.
        - **WinBox GUI (alternative configuration tool)**.
    - Default credentials:
        - **Username:** `admin`
        - **Password:** (blank by default, must be set on first login).
- **Configuring Network Interfaces**
    - MikroTik routers use `ether` names instead of `ethX` (e.g., `ether3`, `ether4`).
    - Running `interface print` displays **available network interfaces**.
    - Running `ip address print` shows currently **assigned IP addresses** (initially empty).
- **Assigning IP Addresses to the Router**
    - External network (`eth3`):
        
        ```
        ip address add address=172.20.X.1/16 interface=ether3  
        ```
        
    - Internal network (`eth4`):
        
        ```
        ip address add address=192.168.X.1/24 interface=ether4  
        ```
        
    - Running `ip address print` again verifies that both IPs were **successfully assigned**.
- **Testing Network Connectivity**
    - The **external Kali machine** pings the MikroTik router (`172.20.X.1`).
    - The **router pings the Kali machine** (`172.20.X.2`) to confirm **bidirectional communication**.
    - The internal Kali or Ubuntu machine pings the **router’s internal IP (`192.168.X.1`)**.
- **Setting Up Internal Ubuntu Web Server**
    - The Ubuntu machine is configured with a **static IP** using Netplan:
        
        ```
        addresses:  
          - 192.168.X.2/24  
        gateway4: 192.168.X.1  
        ```
        
    - `sudo netplan apply` applies the settings, and `ip a` confirms the configuration.
    - `ping 192.168.X.1` ensures the Ubuntu machine **can reach the router**.
- **Starting and Testing the Apache Web Server**
    - The web server is inactive by default; it must be started:
        
        ```
        sudo systemctl start apache2  
        ```
        
    - Running `systemctl status apache2` confirms that **Apache is running**.
    - The Ubuntu machine’s IP (`192.168.X.2`) is tested in a browser to verify **webpage availability**.
- **Configuring MikroTik Router for Port Forwarding**
    - The **router must forward web traffic (port 80) to the internal web server**.
    - In the MikroTik GUI:
        - Navigate to **Quick Set → Port Mapping**.
        - Add a new rule to forward **port 80 (HTTP) from external IP to internal web server** (`192.168.X.2`).
    - Using CLI:
        
        ```
        ip firewall nat add chain=dstnat protocol=tcp dst-port=80 action=dst-nat to-addresses=192.168.X.2  
        ```
        
- **Verifying Routing and Web Access**
    - The **external Kali machine** visits the **team router’s external IP (`172.20.X.1`)**.
    - The MikroTik router forwards requests to **`192.168.X.2`**, displaying the webpage.
    - The **scoreboard updates**, confirming successful **web server configuration**.
- **Ensuring Correct Web Content for Scoring**
    - The scoring server requires a **specific team number displayed on the webpage**.
    - Editing the `index.html` file in Ubuntu:
        
        ```
        sudo nano /var/www/html/index.html  
        ```
        
    - Updating the content to reflect the **assigned team number**.
    - Refreshing the scoreboard verifies **all required conditions are met**.
- **Security Considerations for MikroTik Configuration**
    - MikroTik routers expose **various services**, including:
        - **SSH** (`port 22`)
        - **WinBox (port 8291)**
        - **Telnet (port 23, should be disabled for security)**
    - Running `ip service print` displays active services.
    - **Disabling unnecessary services** enhances security:
        
        ```
        ip service disable telnet  
        ```
        
- **Final Thoughts on MikroTik in Mini Hack**
    - The new MikroTik router **simplifies** setup using GUI options while retaining CLI flexibility.
    - Port forwarding, NAT, and firewall rules **mirror real-world router configurations**.
    - Competitors should practice both **GUI and CLI methods** for better adaptability.
    - Security implications (open services, password handling) must be **carefully considered**.


---
Next in Playlist: [26 Mini Hack Reconfiguration](26%20Mini%20Hack%20Reconfiguration.md)