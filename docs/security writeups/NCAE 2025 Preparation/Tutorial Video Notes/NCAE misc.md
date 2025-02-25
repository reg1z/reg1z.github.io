## Challenges and CTFs
- [NCAE-minihack CentOS](NCAE-minihack%20CentOS.md)
- [Quickdraw Notes](../Quickdraw%20Notes.md)

Specific Tools
- SSH
- DNS
- Linux Network Configuration

---
anti-siphon training
- rita

- logging
## Misc.

##### Questions
- What default programs / commands will be available to us?
- What can we use?
	- Notes? Docs? Keyboards?
- How will we be monitored?

##### Quickdraw Configs
- Change default editor to vi / vim / nvim. NOT nano
- 


##### Quickdraws
- nmap scans for specific situations
- how to quickly enumerate the local network


---
# Playlist Notes

## Tips
- In a competition setting it can be useful to pay attention to what groups are in the sudoers file and what users belong to those groups. Good method of enumeration to find any accounts with elevated perms.
- One method for **disabling user accounts** is changing their login shell entry (from the /etc/passwd file) to `/usr/sbin/nologin`
- Python has useful libraries for emulating certain functionality
	- Libraries
		- `crypt` for encryption functions
			- `crypt.crypt("pass","salt")`
		- `os` for operating system commands and functions
	- to exit python shell use `quit()`
- ⭐ Not every command comes native to any system...

# Scenarios and Commands

## CORE SKILLS
### Shell Operators
- `>` write output to file, overwriting current contents
- >> write output to file, appending to end

### Enumeration
- `whoami`

### User Accounts, Groups, Permissions

#### User Account Operations
- **Creating a user**
	- `adduser <name>`
		- 🔔 *user-friendly, interactive, perl, high-level*
			- ⚠️ NOT ALWAYS INSTALLED ⚠️
		- adds user + group of `<name>`
		- creates a new home dir
		- uses `/etc/skel` to scaffold home folder/configs
	- `useradd`
		- 🔔 *low-level, system-native, non-interactive*
			- config → `/etc/default/useradd`
			- binary compiled with the system
- **Deleting a user**
	- `userdel`
- **And more!**
	- `usermod`
		- Modify a user account
			- "*The usermod command modifies the system account files.*"
		- flags
			- -a → append (without overwriting)
			- -G → add to group. Use with -a to ensure the user is not removed as existing member of other groups
	- `passwd`
		- update user account password
#### Permissions
- ⭐ *KNOWLEDGE TO INTEGRATE*
	- Numeric vs string syntax.
	- Order:
		- rwx | read → write → execute
			- r = 4
			- w = 2
			- x = 1
		- `<prefix bit>` // `<file type>` →  **Owner** → **Group** → **Other**
- *PvP Situations*
	- You might not want anyone to read files in certain dirs
- Commands
	- `chmod <perms> <target_file_or_dir>`

#### Groups
- `/etc/group`  → **groups** config file
- Commands
	- `groups`
		- lists groups target user is member of. Current if no target user specified
	- `id`
		- get user id (uid), group id (gid) number(s) of target. Current if no target

### Sudo Configuration
- `/etc/sudoers`



### Passwords and Shadow Hashes
- `/etc/passwd` → **user account** config file
- `/etc/shadow` → **password hashes** 
	- Structure
		- username → pw hash → 
		- $dollar signs usually indicate/delimit salt added to the password

### Services
When working with services, its important to consider some factors:

- ⭐ **Important Tips** ⭐
	- It can be useful to take **backups** of relevant configuration files
	- Be careful when bringing others' (template) configuration files
	- Learn how to restart the target service WITHOUT restarting the computer
		- What changes require a restart or not?
	- What services rely on others? How might this break things?
	- Is it running by default (@startup) or not?


### Network (Service) Configuration

- ⭐ **Important Tips** ⭐
	- This type of configuration often changes depending on the packages a distro uses to implement certain functionality.
	- You need to learn to differentiate when a system has been configured with a connection and when it hasn't.
		- You need to learn how to configure connections for yourself.
	- Questions to ask // considerations
		- What is the name of the interface for your current distro?
		- Where did your system get an existing ip address from? Which service did the system use to get it?
		- What is the *minimum* necessary configuration required to get this thing working?

- **(Commands) Most Common Configuration Methods**
	- `ifconfig`
		- ⚠️ MOSTLY DEPRECATED
		- Still used in some websites/legacy systems, but it has been superceded by modern alternatives.
		- DOES NOT come installed by default in:
			- Ubuntu → requires apt installing the `net-tools` pkg
		- DOES come install by default in:
			- Kali
		- CANNOT list out **temporary ip addresses**
	- `ip`
		- 🔔 Most common tool often installed by default in the modern era. Usually works across multiple platforms
		- **Subcommands**
			- `ip a` → list out network adapters (**interfaces**)
			- `ip addr add <ip> <where/dev> <name/interface>`
				- adds a **temporary ip address** e.g. the address is not added to any config file
			- `ip addr flush <where/dev> <name/interface>`
				- flush ip addresses on target 
- **Config Files**
	- **interfaces file** (net-tools/ifconfig)
		- `/etc/network/interfaces`
			- only installed if you have the **net-tools** package (ifconfig)
		- Kali → exists by default
		- Restarting the service // service name
			- sudo systemctl restart **networking**
	- CentOS
		- `/etc/sysconfig/network-scripts/` → contains **ifcfg files**
			- This service has 1 file for every interface (unix-centric philosophy)
			- Keywords for individual configs. Checkout an example file on your own.
		- Restarting the service // service name
			- sudo systemctl restart **network**
	- Netplan (Ubuntu)
		- Restarting
			- sudo netplan apply

#### Network Interface Vocab n' Slang
- `lo` → standard name for the **loopback interface**
	- Used for internal testing. For sending signals to yourself.
	- 127.0.0.1/8

 ### NetCat
- picking higher unused ports is better
- 

### systemctl


### Web Stuff
#### Commands
- `curl` → Acronym: "Client for URL" | Easy way to make web requests via CLI
	- ⭐ When you only have a terminal interface, this is useful for testing web connectivity to certain hosts. *e.g. when configuring a centos router...*
- `wget` → Aimed more at downloading things
- `nc` → netcat

#### Web Services
Potential web services:
- httpd
- nginx
- apache2
- check `/etc`

##### apache
- DocumentRoot → location of website existence

Permissions in apache
- 

### Router Configuration
- Keep in mind the concept of **Zones**
	- You can modify particular zones to function as a router
	- But it is probably more efficient to designate a zone for this use-case
		- Such as some previously existing ones already designed for this use case...
			- external and internal
- **Masquerading** is a setting allowing for ***internal devices*** to use the external networks. Enables core (outbound) router functionality.
- **Forwarding** allows for an external request to be forwarded to an internal webserver
	- e.g. **Port Forwarding**
	- ⚠️ You don't want to add a specific service to the router interface doing the forwarding. You want to add the relevant port that the internal webserver is listening on

### CentOS
- firewalld
- `firewall-cmd`
	- ⭐ ALL CHANGES TO CONFIGS VIA COMMANDS ARE TEMPORARY UNLESS USING THE `--permanent` FLAG!!!
		- Doesn't get applied until restart, unlike the instantaneous application when not using this flag
		- Make sure your changes can survive a reload!!!
	- `sudo firewall-cmd --list-all-zones`
	- `sudo firewall-cmd --list-all --zones=<name>`
	- **changing an interface's zone**
		- `sudo firewall-cmd --change-interface=eth0 --zone=external --permanent`
	- **forwarding a port for a given zone**
		- `sudo firewall-cmd --zone=<ZoneName> --add-forward-port=port=<Port#>:proto=<protocol>:toport=<port#>:toaddr=<ipAddress> --permanent`
			- adding extras via `:` is optional. This is a way to target other critera like the protocol used
	- **reloading firewall service**
	- `sudo firewall-cmd --reload`
- Recommended ways for assigning target interfaces to a zone
	- Add the zone to the **ifcfg** file when first configuring the interface
		- `ZONE=internal` // `ZONE=external`
	- Using the `firewall-cmd` command

### `rsync`

rsync for backups

