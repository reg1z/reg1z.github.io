
# Potential System Hardening
**(⭐ = really important omg)**

### Least privilege
- Configure user accounts with unique secure passwords for each member of the team?
	- Should each have sudo/root access?
		- If so, should the sudo password for each be unique?
- ⭐ Change User/Password defaults
	- ⭐ Microtik Router
	- Webserver
	- Kali Machines
	- ???
	- Remove / Disable / Change PWs of any default user accounts

### Automated secure remote backups
- ***Potential Solutions***
	- `rsync` + `ssh` (with PKI keys) + `cron` (taught in NCAE YouTube playlist)
		- Use proper nesting of the `ssh` command in quotes when using rsync via ssh w/ keys (`"ssh -i keyfile"`).
		- What method to use to transfer key(s) to target systems?
		- keep ssh keys for the automated backup using the root account in a separate root-only readable folder?
- ***Should there be backups of...***
	- ssh keys for passwordless access?
	- Entire systems?
		- webserver?
		- router? (How feasible is this w/ the microtik router?)
		- other (???)
- Where should backups be stored? On which host(s)? Multiple hosts?
- Is *encrypting* backups feasible—i.e. is there enough time and compute resources?

### Monitoring
- LOGS 🎶🎸🌲🪓🎸🎶
- ???

### Firewall
- Enable on individual hosts?
- Set up a firewall in front of / behind the router?
- Block icmp traffic (pings)?

### Known Unknowns
- ***Network Topology***
	- IPs (team number) + Netmasks
- ***We will have external internet access, therefore...***
	- Will we need to patch any systems?
		- This could involve running vulnerability scans and deploying patches.
		- If patches are unavailable, will require implementation of compensating controls.
- ***Specific Host Information***
	- How many hosts are in our control?
	- What OS/distro/software do they have?
	- ⭐ ***Services***
		- Which services are configured by default?
		- Which services increase our attack surface?
		- What services are necessary to accomplish our goal(s)?
		- Which services have widely-known default values?
	- ⭐ ***Router***
		- What's allowed through by default?
		- What do we allow through?
		- What do we block?