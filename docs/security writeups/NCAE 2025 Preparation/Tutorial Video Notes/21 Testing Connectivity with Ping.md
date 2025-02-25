# 21 Testing Connectivity with Ping

<iframe src="https://www.youtube.com/embed/DROCT3-hU3c?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

- **Using `ping` to Test Network Connectivity**
    - `ping <IP>` sends test packets to check if a device is reachable.
    - Works for both **internal and external network testing**.
    - Continuous pinging in Linux can be stopped using `Ctrl + C`.
- **Verifying Local Network Connections**
    - `ping <local_IP>` confirms if devices on the **same network** are reachable.
    - Successful responses mean the **network is properly configured**.
    - High latency or dropped packets indicate **network issues**.
- **Detecting Network Separation Issues**
    - `ping` fails if two devices are on **different networks without routing**.
    - The error `Network is unreachable` means the destination **is not accessible**.
    - If the network is reachable but the device is not, the error is `Host unreachable`.
- **Using Ping for Troubleshooting**
    - Helps identify whether an issue is **device-specific or network-wide**.
    - Can be used to test **router and gateway connectivity**.
    - Understanding ping failures helps diagnose **firewall, routing, or misconfiguration issues**.


---
Next in Playlist: [22 Temporary Permanent and Flushing IPs](22%20Temporary%20Permanent%20and%20Flushing%20IPs.md)