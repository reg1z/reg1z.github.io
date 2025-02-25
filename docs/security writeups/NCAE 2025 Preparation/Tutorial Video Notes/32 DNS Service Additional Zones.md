# 32 DNS Service Additional Zones

<iframe src="https://www.youtube.com/embed/y2-w9m4yvqw?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Configuring Additional DNS Clients**
    - The existing **DNS server is hosted on Ubuntu** and resolves internal domains.
    - The goal is to allow **other machines**, like the internal Kali system, to use this DNS service.
    - DNS settings are updated in Kali’s `/etc/resolv.conf` file to point to the Ubuntu DNS server (`192.168.8.2`).
- **Verifying DNS Resolution on Kali**
    - Adding `nameserver 192.168.8.2` to `resolv.conf` directs **DNS queries to the Ubuntu machine**.
    - Testing with `nslookup www.ncaecybergames.org` verifies the resolution.
    - The browser successfully accesses `www.ncaecybergames.org`, confirming DNS functionality.
- **Expanding DNS Records for Additional Services**
    - The DNS server currently resolves only `www.ncaecybergames.org`.
    - To extend functionality, **more records must be added** for other services like the scoreboard.
    - The **scoring server** is externally hosted (`172.20.0.1`), and a new subdomain (`score.ncaecybergames.org`) is assigned to it.
- **Updating the Forward Lookup Zone**
    - The forward lookup file (`/etc/bind/zones/forward.ncaecybergames.org`) is modified.
    - A new `A` record is added:
        
        ```
        score IN A 172.20.0.1  
        ```
        
    - The serial number in the file is incremented before saving.
- **Restarting and Testing the Updated DNS Service**
    - The DNS service is restarted using `sudo systemctl restart named`.
    - Running `nslookup score.ncaecybergames.org` confirms that it now resolves to `172.20.0.1`.
    - Accessing `score.ncaecybergames.org` in a browser shows the **scoring page**, confirming success.
- **Implementing Reverse DNS for Scoreboard Domain**
    - Reverse DNS allows resolving an IP **back to a domain name**.
    - The `/etc/bind/named.conf.default-zones` file lacks a record for the `172.20.0.x` network.
    - A new reverse zone entry is created for `172.20` using the `arpa` format.
- **Modifying the Reverse Lookup Zone File**
    - The file `/etc/bind/zones/reverse.ncaecybergames.org` is updated to include:
        
        ```
        1.0 IN PTR score.ncaecybergames.org.  
        ```
        
    - The serial number is incremented, and the file is saved.
- **Applying Reverse DNS Changes**
    - The DNS service is restarted again: `sudo systemctl restart named`.
    - Running `nslookup 172.20.0.1` confirms the reverse lookup now maps to `score.ncaecybergames.org`.
- **Final Testing and Browser Validation**
    - The updated DNS server now resolves both forward (`score.ncaecybergames.org → 172.20.0.1`) and reverse (`172.20.0.1 → score.ncaecybergames.org`).
    - Other devices on the network can now use the **configured DNS service** to resolve names.
    - A browser test confirms seamless access to the scoreboard using its domain instead of an IP address.

---
Next in Playlist: [33 DNS Service Through The Router](33%20DNS%20Service%20Through%20The%20Router.md)