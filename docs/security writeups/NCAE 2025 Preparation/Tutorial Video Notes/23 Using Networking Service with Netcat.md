# 23 Using Networking Service with Netcat

<iframe src="https://www.youtube.com/embed/_aIac8hweAg?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Understanding Netcat (`nc`) for Network Testing**
    - `nc` (Netcat) is a low-level tool for **sending and receiving network data**.
    - Commonly used for **manual service testing** and **network diagnostics**.
    - Works without the complex processing of web browsers or other services.
- **Setting Up a Netcat Server**
    - `nc -l <port>` starts a **listener** (server) on a given port.
    - Example: `nc -l 54321` listens for connections on port `54321`.
    - Servers require **an IP address and an open port** to accept connections.
- **Connecting a Client to the Server**
    - `nc <server_IP> <port>` connects a client to a **Netcat server**.
    - Example: `nc 192.168.118.100 54321` establishes a connection.
    - Once connected, text sent from one machine **appears on the other**.
- **Understanding Ports and Services**
    - Services use ports to determine **which application handles data**.
    - Standard ports include **80 (HTTP), 443 (HTTPS), and 22 (SSH)**.
    - Unregistered ports (above `1024`) can be used for **custom services**.
- **Using Netcat for Remote Command Execution**
    - `nc -l -p <port> -e /bin/bash` redirects input to a **bash shell**.
    - Example: `nc -l -p 54321 -e /bin/bash` allows **remote command execution**.
    - This method can be exploited for **unauthorized remote access**.
- **Preventing Netcat Exploits**
    - Restricting open ports prevents **unauthorized remote connections**.
    - Firewalls and security policies should block **unnecessary services**.
    - Running `nc -l -p <port>` in a loop (e.g., via Python) **creates persistent backdoors**.


---
Next in Playlist: [24 Web Services with Apache](24%20Web%20Services%20with%20Apache.md)