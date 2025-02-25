# NICE Challenge: Network Admin Crash Course | Mike Morris

# Tasks:
⭐ Many resources are on the Workstation-Desk flashdrive.

## Order Presented
### Firewall
- Correct port forward issues @takasaka had. Prod-Web is supposedly not accessible from outside the internet (but the website hasn't launched yet)
- Inspect the firewall rules in pfSense
	- Depending on the state of the firewall, either backup or restore (previous backup of) firewall rules
		- backups are always stored in `/ftp`
	- Set up **port forwarding** for the **production server** like @takasaka was attempting
- Set up useful data in dashboard on pfsense
- Set up **Snort rules on the same host as Firewall**
	- Update pfSense to latest ver and reinstall Snort.
		- Make sure the update doesn't get rid of any packages.
			- an update once caused snort and sudo to both be missing. make sure to reinstall them if need be.
	- The rules are for the **LetMeCry** exploit.
	- **Make sure to place them on an interface where they'll actually trigger**
	- Enable the option allowing snort to send alerts to its system log.

### Misc Tasks:
- **Dev-Web** can't talk to **Database** and @gbates can't get **DNS** to resolve.
    - The issue could be
        1. Dev-Web
        2. Database
        3. Domain-Controller
        4. All of the above (maybe)
- "config a couple machines to communicate via ipv6". The flashdrive has a text file with their names.
- fix "some" linux machine whose host firewall is blocking all traffic. also check the flashdrive.

## Re-ordered
Firewall
- Ensure Backup's open ports are correctly configured. This enables necessary fixes + the safe transfer of the backup files. 
- Update pfSense to latest ver and reinstall Snort.
	- Make sure the update doesn't get rid of any packages.
		- an update once caused **snort** and **sudo** to both be missing. make sure to reinstall them if need be.

- Inspect the firewall rules in pfSense
	- Depending on the state of the firewall, either backup or restore (previous backup of) firewall rules
		- backups are always stored in `/ftp`
		- from requests.txt: "***There is a backup of the Firewall rules on Backup in /ftp. Please restore pfSense's firewall rules from it***"
	- Set up **port forwarding** for the **production server** like @takasaka was attempting
	- configure IPv6 rules as per ipv6_scheme.txt
		- Development env
			- Firewall
			- Database
		- Internal env
			- Firewall
			- Mail
- Set up useful data in dashboard on pfsense
	- interface statistics widget (requests.txt)

- Set up **Snort rules on the same host as Firewall**
	- The rules are for the **LetMeCry** exploit.
	- **Make sure to place them on an interface where they'll actually trigger**
	- Enable the option allowing snort to send alerts to its system log.


## Steps Taken:
First, I made a bulleted checklist of specific tasks in some note-taking software to facilitate re-arranging each task into the appropriate order.

Then, I checked the files on the flashdrive at Workstation-Desk to see if any info they contained might affect how early or late in the checklist I should implement certain changes.

ipv6_scheme.txt:
```
The IPv6 scheme that will be used for the development network is:

fda5:1d93:2e24:df8f::/64

Firewall = fda5:1d93:2e24:df8f::0001
Database = fda5:1d93:2e24:df8f::0002

fda5:1d93:2e24:134a::/64

Firewall = fda5:1d93:2e24:134a::0001
Mail = fda5:1d93:2e24:134a::0002
```

requests.txt:
- There is a backup of the Firewall rules on Backup in /ftp. Please restore pfSense's firewall rules from it
- pfSense dashboard config:
	- interface statistics widget
- Configure IPv6 according to the details laid out in ipv6_scheme.txt
- Backup seems to be ahving problems with its firewall configuration. Ensure that traffic is only allowed through on ports 21, 22, and 80.
- As you make changes to all the host firewalls, make sure that they still have secure rules. This means you should only allow `ssh` traffic along with traffic on any ports required for the primary services offered by that host.
	- However, our MSP has requested we ensure that each host can still be pinged, so please take that into account while accomplishing your work.


Since many of these tasks are dependent on the router—and that the process of updating the router risks loss of data—it was evident that beginning with the router update would be the best starting point to set a solid foundation for all additional configurations needing to be made in pfSense for the relevant checks.

Prior to this however, I addressed corrected issues with the host firewall of "Backup," as it would both check a task off the list AND ensure the secure delivery of firewall backup files via `ssh`/`scp` to the Network's Firewall.

...