
### Misc. Things
- May want to learn GNU nano in case vi / vim is ever unavailable.
- Learn enhanced curl commands
- In this case we're using **firewalld**. What are the other common firewall services used in linux/unix environments?
- DNS


### Notes
- Config network settings for each VM
	- Kali external/internal + CentOS Router + Ubuntu internal server
	- interfaces / IPs + individual misc. settings per host
- VM Hosts
	- CentOS Router
		- Steps:
			- Network Configs (`/etc/sysconfig/network-scripts/`) ← location of ifcfg files
				- external interface
					- BOOTPROTO=static (no dhcp server)
					- ONBOOT=yes
					- Set IP address. This will become the internal network's **default gateway**
						- IPADDR=external network ip
						- NETMASK=255.255.0.0
					- ZONE=external
					- `firewall-cmd`
						- port forwarding
				- internal interface
					- BOOTPROTO=static (no dhcp server)
					- ONBOOT=yes
					- Set IP address. This will become the internal network's **default gateway**
						- IPADDR=internal network ip (default gateway)
						- NETMASK=255.255.255.0
					- ZONE=internal
					- masquerading
			- 
		- **ifcfg files** for configuration of network interfaces
		- `firewall-cmd`
	- Ubuntu w/ Apache webserver (ubuntu host)
		- Steps:
			- Network Configs defined in netplan YAML file (`/etc/netplan/01-network-manager-all.yaml`)
				- ethernets:
					- ens18:
						- addresses:
							- `- 192.x.x.x/24`
						- gateway4: `192.x.x.x/24`
				- `sudo netplan apply`
			- change index.html content to team number
			- enable and start the apache2 web service
		- uses **Netplan** for network settings (ubuntu)
		- configure its **default gateway** using the **router address**
			- This will cause the internal ubuntu server to send outbound traffic to the **default gateway/router** when traffic sent does not have an existing valid recipient on the current network segment
			- **Masquerading** (enabled on the router's internal zone) then allows this traffic to be directed to outside networks (this is a type of NAT)
	- Kali External
		- Steps
			- network config in `/etc/network/interfaces`
				- static interface (iface eth0 inet static)
				- set IP (address)
				- set subnet mask (netmask)
				- **DOES NOT need a default gateway**. There is no other router for it to use
	- Kali Internal (not needed for scoring of initial minihack challenge itself)
		- Steps
			- network config in `/etc/network/interfaces`
				- static interface (iface eth0 inet static)
				- set IP (address)
				- set subnet mask (netmask)
				- set default gateway (gateway)



