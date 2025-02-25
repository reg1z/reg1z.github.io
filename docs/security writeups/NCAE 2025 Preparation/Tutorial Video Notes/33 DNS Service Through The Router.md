# 33 DNS Service Through The Router

<iframe src="https://www.youtube.com/embed/AdPaZOU-ngM?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Allowing External DNS Queries Through the Router**
    - The internal DNS server works for local devices, but external queries must be forwarded through the router.
    - The goal is to enable an **external Kali machine** to query the **internal DNS server** via the router.
    - Currently, external devices use IP addresses instead of **domain names** due to lack of DNS resolution.
- **Configuring the External Kali Machine for DNS Queries**
    - The external Kali machine must be configured to **use the router as its DNS server**.
    - `sudo nano /etc/resolv.conf` is used to update the nameserver entry.
    - The router's **external IP (172.20.x.1)** is set as the nameserver since Kali cannot see internal IPs.
- **Testing External DNS Resolution**
    - Running `nslookup www.ncaecybergames.org` from the external Kali machine **fails** initially.
    - The query reaches the router but does not continue to the **internal DNS server**.
    - The failure is expected because **DNS forwarding is not yet configured** on the router.
- **Forwarding DNS Requests from the Router**
    - The router must forward **DNS traffic (port 53) from external devices** to the internal DNS server.
    - The command used is:
        
        ```
        sudo firewall-cmd --zone=external --permanent --add-forward-port=port=53:proto=tcp:toport=53:toaddr=192.168.x.2  
        ```
        
    - This rule attempts to forward **TCP-based DNS traffic**, but it does not work.
- **Understanding DNS Protocol Requirements**
    - DNS primarily uses **UDP**, not TCP, for standard queries.
    - The existing rule only forwards **TCP-based requests**, leading to **failed lookups**.
    - Many users mistakenly assume DNS operates on **TCP by default**.
- **Fixing the DNS Forwarding Rule**
    - The incorrect rule is removed using:
        
        ```
        sudo firewall-cmd --zone=external --permanent --remove-forward-port=port=53:proto=tcp  
        ```
        
    - The corrected rule is applied with **UDP forwarding**:
        
        ```
        sudo firewall-cmd --zone=external --permanent --add-forward-port=port=53:proto=udp:toport=53:toaddr=192.168.x.2  
        ```
        
    - The firewall settings are reloaded: `sudo firewall-cmd --reload`.
- **Verifying External DNS Query Success**
    - Running `nslookup www.ncaecybergames.org` again on the external Kali machine now **resolves correctly**.
    - The external Kali machine does not see the internal DNS server directly—it only queries the router.
    - The router transparently forwards the query to the internal DNS server and relays the response.
- **Limitations of Forwarding Internal DNS Queries**
    - Some internal addresses (e.g., `192.168.x.x`) cannot be accessed externally even if resolved.
    - Queries for `www.ncaecybergames.org` resolve successfully, but the external Kali machine may **not reach** internal sites.
    - Queries for externally hosted domains (e.g., `score.ncaecybergames.org`) work since they resolve to **reachable IPs**.
- **Testing Browser-Based Access to the Scoreboard**
    - Opening `score.ncaecybergames.org` in a browser from the external Kali machine now **works correctly**.
    - A certificate warning appears since the connection is over HTTPS, but it can be bypassed.
    - The scoreboard is now accessible using **domain names instead of IPs**, improving usability.
- **Best Practices for DNS Forwarding and Security**
    - Always ensure **UDP forwarding** for DNS instead of TCP.
    - Be mindful of which DNS queries are **internally vs. externally accessible**.
    - Testing DNS resolution **step by step** (local, internal, external) helps **debug issues efficiently**.
    - Proper DNS configuration improves **usability and security** while reducing reliance on direct IP addresses.


---

Next in Playlist: [34 Rsync Service Basics](34%20Rsync%20Service%20Basics.md)