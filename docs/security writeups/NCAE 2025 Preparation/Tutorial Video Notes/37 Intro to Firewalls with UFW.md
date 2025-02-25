# 37 Intro to Firewalls with UFW

<iframe src="https://www.youtube.com/embed/DAaLyKDzxl4?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Introduction to Firewalls and UFW**
    - Firewalls are a **critical security defense** in cybersecurity, controlling inbound and outbound traffic.
    - The **Mini Hack environment** includes two internal machines: **Ubuntu (192.168.195.2)** and **Kali (192.168.195.100)**.
    - The focus is on **configuring UFW (Uncomplicated Firewall)** on Ubuntu to secure network traffic.
- **Understanding Linux Firewall Options**
    - Linux offers multiple firewall solutions:
        - **iptables** (powerful but complex).
        - **firewalld** (used in CentOS).
        - **UFW** (user-friendly, used in Ubuntu).
    - UFW simplifies firewall management by **abstracting complex iptables rules**.
- **Checking and Enabling UFW**
    - Checking firewall status:
        
        ```
        sudo ufw status  
        ```
        
    - If inactive, enable UFW:
        
        ```
        sudo ufw enable  
        ```
        
    - Once enabled, UFW starts **blocking inbound traffic by default** while allowing outbound connections.
- **Creating Basic Firewall Rules**
    - Firewalls operate based on **rules** to allow or deny traffic.
    - Example: Allowing trusted traffic from the **internal Kali machine**:
        
        ```
        sudo ufw allow from 192.168.195.100  
        ```
        
    - Blocking traffic from the **entire 192.168.195.0/24 network**:
        
        ```
        sudo ufw deny from 192.168.195.0/24  
        ```
        
- **Rule Processing Order in UFW**
    - **Rules are processed in the order they are created**.
    - If a **deny rule is created before an allow rule**, the allow rule may become **ineffective**.
    - To check processing order:
        
        ```
        sudo ufw status numbered  
        ```
        
- **Allowing Specific Services**
    - Instead of specifying ports, UFW has **predefined service names**:
        
        ```
        sudo ufw allow ssh  
        sudo ufw allow http  
        sudo ufw allow https  
        ```
        
    - These commands open **ports 22 (SSH), 80 (HTTP), and 443 (HTTPS)** for incoming connections.
- **Managing IPv6 Rules**
    - UFW automatically creates **IPv6 rules** alongside IPv4.
    - If IPv6 is **not in use**, unnecessary rules should be **removed** to reduce the attack surface.
    - Deleting an IPv6 rule:
        
        ```
        sudo ufw delete <rule_number>  
        ```
        
- **Understanding Default Rules and ICMP (Ping) Behavior**
    - By default, UFW allows **ping (ICMP) requests**, making the machine discoverable.
    - Checking predefined firewall rules:
        
        ```
        cat /etc/ufw/before.rules  
        ```
        
    - To **disable ping responses**, edit `/etc/ufw/before.rules` and change **ACCEPT to DROP** under the ICMP section.
    - Reload the firewall to apply changes:
        
        ```
        sudo ufw reload  
        ```
        
- **Testing and Troubleshooting Firewall Rules**
    - Running `sudo ufw status verbose` shows detailed rule configurations.
    - If SSH access is blocked, temporarily disable UFW:
        
        ```
        sudo ufw disable  
        ```
        
    - To reset UFW to its default state:
        
        ```
        sudo ufw reset  
        ```
        
- **Final Thoughts on UFW and Network Security**
    - UFW is a **user-friendly way** to secure Ubuntu-based servers and workstations.
    - Understanding **how rules process and interact** prevents conflicts and misconfigurations.
    - In competitions, firewalls should be configured to **allow only necessary traffic** while blocking unauthorized access.


---
Next in Playlist: [38 Active Connection Defense](38%20Active%20Connection%20Defense.md)