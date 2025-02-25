# 38 Active Connection Defense

## Tools

### `netstat`
Lists out network connection statistics

- `netstat -tu` -> filter only connections to tcp and udp 
	- -tun -> resolve names to corresponding port
	- -tuna -> also print out listening connections
	- -tunap -> also get process ids (PID) for each connection process. requires sudo
- `netstat | grep ESTABLISHED`

### `ss`
Similar to `netstat`. Alternative

### `kill`
Kill malicious processes / red team connections!

- `kill <pid>`
- 

### `pkill`
Similar to `kill`, allowing for more specific targets.
- killing by userid/name, etc...
- Don't accidentally kill your own/team's sessions!

### `w`
Shows who is logged in and from where

### `top` / `htop`
A lot like task manager, but in the CLI


### `ps`
Search active processes. Nuanced options


## Communication with users / teammates!

### `wall`
"Broadcasts" a message to all users
- `wall "Server shutting down in 5 minutes. Please save your work.`

### `write`
Send basic DMs to a target user.
- `sudo write bob pts/2`

## Red Flags
- random scripts running in the background
- new malicious cronjobs

---

# 38 Active Connection Defense

<iframe src="https://www.youtube.com/embed/37-6lgYtGGw?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Monitoring Active Connections for Security**
    - Attackers often maintain **active connections** to compromised systems.
    - Monitoring tools help identify **who is connected** and **what they are doing**.
    - The **Kali machine** is set up as a **server**, while Ubuntu users log in remotely.
- **Creating Test Users for SSH Connections**
    - `sudo adduser Bob` creates a new user **Bob** with a basic password.
    - `sudo adduser Jenny` adds another user to simulate **multiple remote sessions**.
    - The Ubuntu machine initiates SSH connections to **simulate attacker activity**.
- **Using Netstat to View Active Connections**
    - `netstat -tuna` lists all **TCP and UDP connections**.
    - The output shows:
        - **Local Address:** The listening interface and port.
        - **Foreign Address:** The remote user's IP and port.
        - **State:** Whether the connection is **established, listening, or closed**.
- **Filtering Netstat Output for Better Readability**
    - `netstat -tunanp` includes **process IDs (PIDs)** of active connections.
    - The `-n` option prevents **DNS resolution**, improving performance.
    - Pipe output to `less` or `grep` to **quickly find specific connections**.
- **Identifying and Terminating Unauthorized Users**
    - Attackers often maintain SSH sessions **to retain access**.
    - Find the attacker's **process ID (PID)** using Netstat.
    - `sudo kill <PID>` terminates the connection **immediately**.
- **Logging Out Users with the `pkill` Command**
    - Instead of killing individual PIDs, `pkill -u <username>` logs out **all active sessions** for a user.
    - Useful for **removing compromised accounts quickly**.
    - Confirm logout by rerunning `w` or `netstat`.
- **Using the `w` Command to List Logged-In Users**
    - `w` displays **active sessions, their originating IPs, and the processes they are running**.
    - Differentiates between **local users and remote attackers**.
    - Helps decide which connections should be **terminated**.
- **Blocking Suspicious IPs with UFW**
    - `sudo ufw deny from <suspicious_ip>` prevents **future unauthorized connections**.
    - UFW (Uncomplicated Firewall) **restricts access** to known good addresses.
    - Combining UFW with **SSH key authentication** enhances security.
- **Sending Messages to Active Users**
    - The `wall` command sends **a broadcast message to all logged-in users**:
        
        ```
        sudo wall "System rebooting in 5 minutes. Save your work."  
        ```
        
    - The `write` command sends **direct messages to specific users**:
        
        ```
        sudo write <user> <terminal>  
        ```
        
    - Useful for **alerting teammates before taking security actions**.
- **Ensuring Long-Term Security with Proactive Monitoring**
    - Regularly **checking active connections** prevents stealthy backdoors.
    - `netstat`, `w`, and firewall rules help **quickly respond to live attacks**.
    - Combining **reactive defense (kill, pkill) with proactive measures (UFW, key-based SSH)** ensures a **more secure system**.

---
Next in Playlist: [39 Scripting Hello World](39%20Scripting%20Hello%20World.md)