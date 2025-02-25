# 31 DNS Service Basics

<iframe src="https://www.youtube.com/embed/mpVX4jxF4ww?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Introduction to DNS Basics**
    - DNS (Domain Name System) is one of the **most challenging services** to configure.
    - It maps **domain names to IP addresses** (forward lookup) and **IP addresses to domain names** (reverse lookup).
    - DNS servers answer queries from **client computers** based on stored records.
- **Types of DNS Lookups**
    - **Forward Lookup:** Converts **domain names** into **IP addresses** (e.g., `ncaecybergames.org` → `192.168.2.1`).
    - **Reverse Lookup:** Converts **IP addresses** into **domain names** (`192.168.2.1` → `ncaecybergames.org`).
    - Both lookups require proper **zone file configuration**.
- **DNS Software Used in Mini Hack**
    - The `bind` service is commonly used to configure a **DNS server**.
    - Configuration files for `bind` are typically found in `/etc/bind/` (Ubuntu) or `/etc/named/` (CentOS).
    - The service is managed using `systemctl status named` to check if it’s running.
- **Finding and Editing DNS Configuration Files**
    - The primary configuration file for `bind` is `named.conf`, found in `/etc/bind/`.
    - Additional configurations are stored in files like `named.conf.options`, `named.conf.local`, and `named.conf.default-zones`.
    - Some settings are **included from external files** to allow modular configuration.
- **Setting Up a Forward Lookup Zone**
    - The forward zone **maps domain names to IP addresses**.
    - The entry format:
        
        ```
        zone "ncaecybergames.org" {  
            type master;  
            file "/etc/bind/zones/forward.ncaecybergames.org";  
        };  
        ```
        
    - This configuration tells the DNS server to refer to `forward.ncaecybergames.org` for domain mappings.
- **Setting Up a Reverse Lookup Zone**
    - The reverse zone **maps IP addresses to domain names**.
    - The entry format:
        
        ```
        zone "8.168.192.in-addr.arpa" {  
            type master;  
            file "/etc/bind/zones/reverse.ncaecybergames.org";  
        };  
        ```
        
    - The IP address **must be written in reverse order**, following the `arpa` notation.
- **Creating Forward and Reverse Lookup Files**
    - The forward lookup file contains **A records**, associating names with IPs:
        
        ```
        www IN A 192.168.8.2  
        sandbox-ubuntu IN A 192.168.8.2  
        ```
        
    - The reverse lookup file contains **PTR records**, associating IPs with names:
        
        ```
        2 IN PTR www.ncaecybergames.org.  
        2 IN PTR sandbox-ubuntu.ncaecybergames.org.  
        ```
        
- **Applying DNS Configuration Changes**
    - Restart the DNS service after modifying configurations:
        
        ```
        sudo systemctl restart named  
        ```
        
    - Verify its status with:
        
        ```
        sudo systemctl status named  
        ```
        
    - Any syntax errors will **prevent the service from starting**.
- **Testing DNS Resolution**
    - Use `nslookup` to test the DNS queries:
        
        ```
        nslookup www.ncaecybergames.org  
        nslookup 192.168.8.2  
        ```
        
    - If configured correctly, the DNS server will return the expected mappings.
- **Updating DNS Resolver Settings**
    - The system must know where to **send DNS queries**.
    - The file `/etc/resolv.conf` should include the DNS server’s IP:
        
        ```
        nameserver 192.168.8.2  
        ```
        
    - Alternatively, the network configuration (`/etc/netplan/`) can be updated to specify the DNS server.
- **Final DNS Testing**
    - Refreshing a web browser with `www.ncaecybergames.org` should load the correct webpage.
    - Reverse lookups should successfully return **the domain associated with the IP**.
    - A properly configured DNS server enables **efficient domain resolution in the Mini Hack environment**.

---

Next in Playlist: [32 DNS Service Additional Zones](32%20DNS%20Service%20Additional%20Zones.md)