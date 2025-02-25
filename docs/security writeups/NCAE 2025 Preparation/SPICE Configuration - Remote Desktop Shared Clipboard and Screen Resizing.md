# SPICE Config
*Shared Clipboard (copy/paste) & Automatic Screen Resizing*

## **TO PREPARE:**
- Install `virt-viewer` on the ==**Local** PC / VM== you'll be using to compete.
	- **Link (scroll down):** https://virt-manager.org/download
		- .MSI installer for Windows
		- .tar.xz for UNIX
	- Available on the default repos in most popular Linux distros via package manager install (`apt` / `yum` / `dnf` / `pacman` / etc... )

## **TO CONNECT:**
- Select "SPICE" from the drop-down in proxmox for the target host you'd like to connect to.
- A file should automatically be downloaded.
- Double-click this file. If virt-viewer is installed, it should automatically connect to the cloud host via SPICE.
![Pasted image 20250222152539](../../assets/images/Pasted%20image%2020250222152539.png)


## **ON GAME DAY:**
### ***NOTE:** Only applied to Kali hosts in both Mini Hack challenges (this could be different on game day)*

- Enable the **spice-vdagent** on necessary hosts by using the following commands ==WITHIN== the ==CLOUD HOSTS (Kali machines).==

**Commands:**
```bash
sudo systemctl enable spice-vdagent
sudo systemctl start spice-vdagent
```
- It should work once enabled after relogging in.