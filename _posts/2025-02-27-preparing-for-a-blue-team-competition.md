---
layout: post
title: "Preparing for a Blue Team Competition"
tags:
  - cybersecurity
  - blueteam
  - competitions
  - NCAE
  - linux
date: 2025-02-27
categories:
toc:
description:
---
This past February, I began volunteering in WGU's Cyber Club. This afforded the opportunity to participate in the [2025 NCAE Cybergames](https://www.ncaecybergames.org/). It's a single-day blue team-oriented competition aimed at first-time competitors. This is one of my first experiences taking part in a team-based defensive engagement like this. Our teams have yet to compete, but have been hard at work preparing.

[The NCAE has its own YouTube playlist](https://www.ncaecybergames.org/tutorials/) that covers fundamental Linux skills. It is high-level, comprehensive, and lengthy. While it's a great introduction, it doesn't give obvious hints as to the vast amount of other knowledge a team might want to consider after watching.

As someone with a previous background in software development, I like to think of myself as fairly capable at the terminal—and with tech in general—but nothing *truly* prepared me for the open-endedness of all the potential skills a team could bring in. There are an overwhelming amount of approaches one could take. In essence, it was difficult for me to come up with any kind of "comprehensive" practice plan.

So, in addition to my own research, I sought the help of others. Here's what they told me. Keep in mind, this competition mostly uses Linux hosts. I do not give Windows-specific advice in this article.

> [!tip]+ Credits
> Shoutout to these folks for taking the time to offer their expertise!
> 
> - **w33t** → [https://w33t.io/](https://w33t.io/)
> - **echotango** → (the Internet)

## Core Skills

### 0) Research / OSINT Skills
Knowing how to quickly and tactically prompt search engines and various other tools can get you needed information fast. Knowing when to question results is just as important. This isn't "formal" research, rather it's the proverbial "google-fu."

When you don't know something, you should be prepared to figure it out on-the-fly.

### 1) Conceptual Knowledge
These include fundamental concepts and/or frameworks within the fields of Network and Security. Without at least a surface level understanding of these, you might find it difficult to communicate with team members about specific elements of the engagement.

- **The TCP/IP Model**
	- The OSI Model, while popular, is not how the Internet actually works (ask John Strand).
- **Least Privilege**
- **System Monitoring**
- **Network Monitoring**
- ...

### 2) Linux Fundamentials
In a competition like this, one will feel dead in the water without some rudimentary knowledge of the Linux command-line. *Ideally*, you'll have some passing knowledge of the general system as a whole.

I've done my best to order them by priority.

1. **Navigating the Linux Command-line and File structure**
	- Basic filesystem navigation via terminal
		- `cd` → change directory
		- `ls` → list files
	- Basic file interaction
		- `cat` → print file contents to stdout
		- `cp` → copy files
		- mv → move (and/or rename) files
	- Basic understanding of the [Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
2. **Bash**
	- Overall syntax
	- Operators
	- stdout VS stdin VS stderr
	- Input & output redirection
	- Piping input & output
3. **Users and Groups; `sudo`**
4. **Process management**
	- `ps` → list processes
	- `kill` → kill target process
5. **Service configuration**
	- systemctl
	- systemd (to a minimal extent)
	- ...
6. **Networking and Protocols**
	- See below: Knowledge of protocols
	- Opening/closing ports.
	- DNS Configuration. The NCAE uses `bind` to manage DNS in their tutorial videos.
	- Routing
7. ...

### 3) Knowledge of Communication Protocols
A few of the previously mentioned Linux skills require some familiarity with widely used communication protocols. If you're contributing to your team's Network Configurations, it will be crucial to have an understanding of the protocols you'll be using. This will usually be one or more of the following. **Note:** *A comprehensive knowledge of each protocol IS NOT required—you just need to know enough to acquire the skills necessary to protect your environment*.

- No matter what, you should know what these are.
	- **TCP** → Transmission Control Protocol
	- **UDP** → User Datagram Protocol
	- **IP** → Internet Protocol. IPv4; perhaps IPv6 if it is within scope of the competition.
	- **ICMP** → Internet Control Message Protocol
	- **SSH** → Secure Shell protocol

- You should know what these are, but can tailor what you study based on your individual responsibilities within the team. These protocols are likelier than most to apply.
	- **DNS** → Domain Name System protocol
	- **FTP** → File Transfer Protocol
	- **SSL/TLS** → Secure Sockets Layer / Transport Layer Security
	- ...

- These may not always apply. Depends on the scenario's design.
	- **NFS** → Network File System
	- **SMB** → Server Message Block
	- **Syslog**
	- ...

## Gaining a Competitive Edge

This is a BARE BONES list. If using it, you will want to dive deeper into each topic, perhaps seeking the direct advice of someone with more experience.

If you are expecting *competitive* results in an engagement like this, you will need to come up with creative solutions.

In the case of the NCAE, teams are given external network access. There are few restrictions on the tools you can import into the environment. The one caveat is that all tools/scripts/software you use must either be disclosed or already known to the general public.

Don't assume you'll be able to bring in *any* cutting edge defensive solution though. You usually don't know what the state of each endpoint in your environment will be. The NCAE's practice environment (the "Mini Hack") is configured to use Kali Linux 2021.1 as its attack box. You wouldn't be able to easily install additional tools on such a host because Kali is a rolling distribution and its package repositories will outright refuse any request to download something to your insecure system. If you *could* download packages safely, there would be no gaurantee they'd be compatible, since your system is so out-of-date in the first place. This is all seemingly by design, of course. The event coordinators WANT you to get creative. So much so that in cases like this, they will downright FORCE you to.

Realizing this, our teams started brainstorming. We also sought the advice of some awesome security professionals who were more than willing to give their advice. Thank you to w33t and echotango!

### Ideas Generated
This is a growing list. There is no particular order.

- **Find a way to build a shared cloud sandbox environment for practice**
	- Digital Ocean + Terraform?
- **Come up with a list of IoCs to triage (Indicators of Compromise)**
	- What IoCs are associated with the largest risks?
	- `netstat` and `ss` are good for spotting certain IoCs
- **Pre-built scripts & configs**
	- Pre-configuring an [Ansible](../My%20Notes/Unsorted/Ansible.md) Playbook to automate the setup of user accounts, groups, and other tools. Ansible can be executed from a player's local PC via SSH, which would ensure compatibility with a wide number of hosts.
	- Pre-built bash scripts for initial setup configuration. These could also be used with ansible.
		- Configure user permissions with least privilege in mind.
	- Define a secure, effective **SSH config file**.
	- **Vulnerability analysis** script / method.
- **System & Network Monitoring**
	- Using **syslog** for simple, compatible system and network monitoring. This setup could also be automated.
- **Deterrance**
	- Per host firewalls?
		- IPtables/ufw/etc might be useful to configure, when available.
- **Operational Security**
	- Each user should have their own unique secure password memorized or written down. They may want a second password in case the first is compromised.
	- We need a secure way to share passwords
	- `ssh` keys? How can we securely use them w/o needing password configuration?
		- We don't want private keys to be compromised. Use extreme caution if using them on vulnerable hosts.
	- We may want to take regular backups. Perhaps not full backups. Backups should ideally be stored on a secure host, if possible.
		- An alternative would be to record a hash (SHA256, etc) of a backup file to ensure integrity before utilizing it.
- **Least Privilege**
	- We might want to tailor folder and file permissions according to specific roles/users
- **Monitoring Processes**
	- Using `lsof` to find open backdoors and other connections.
		- `lsof -i -n`
		- `lsof -p <process id>`
		- `ls /proc` to view the contents of the process id folder
	- Running `strings` on exe file on memory
	- Pay attention to where process files are/were invoked.
		- `/proc/<processID>/cmdline` → you can cat these files
- **Having knowledge of some commonly used services could be useful even if they haven't been explicitly mentioned by the competition organizer(s)**
	- nginx
	- database solutions → SQL, postgres, flask, etc.
	- certificate services → certbot
		- ==Make sure to perform **dry runs** to minimize risk of rate limits, etc.==

#### Roles
Work-in-Progress. To facilitate implementation of complex systems, teams might want to delegate tasks to particular roles.

- Someone to monitor connections for potential attacks and intrusions.
- and more...

#### Engagement Playbook
Work-in-Progress. A series of consecutive steps to carry out upon connecting to the environment. These are roughly ordered, subject to change. Each member of the team might have their own specific playbook to carry out tasks assigned to them. ==Coordination is key. Make sure your actions don't conflict with others!==

- Ensure `spice-vdagent` is configured on applicable hosts. We want shared clipboard functionality working.y
- Copy/paste a user setup script to get user accounts/groups accessible as quick as possible?
- Set up external Internet connection to Kali machine via the router. Initially, only the router will have external network access.
- `ssh` into Kali machine and execute Ansible Playbooks to setup the environment.
- Enumerate / inventory hosts and systems. Perform a vulnerability analysis of each.
- Take initial backups where necessary. Take them manually with rsync. We might want to keep this process manual rather than use cron.
- Remediate discovered vulnerabilities wherever possible. Reduce attack surface. Harden systems.
	- Ensure that known password vulnerabilities are eliminated ASAP.
	- If a new vulnerability is discovered on a single host, be sure to check all hosts for it.
- Setup syslog or other chosen network monitoring solution. Perhaps use a pre-built script/playbook after having accounted for all hosts.

#### General Tips
- When you have *lots of options* to pick from, don't consider *too many* all at once. You will experience [Choice Paralysis](../My%20Notes/Terminology/Choice%20Paralysis.md). At times it's best to pick a certain tool just to get experience with it. If it's not working out, go to the next thing on the list.
- The Black Team is usually there to help when needed.

## Fin
That's all I have for now, but I'll be updating the blog as preparations continue. You can see my [index](../My%20Notes/NCAE%202025%20Preparation%20🛡️/index.md) page for comprehensive links to my prepatory documents.

There is *much* more knowledge I could cover in preparing for an event like this. But, as is always the case in security, to stay up-to-speed you'll always need to be learning. Security is never a gaurantee. All you can do build the best castle you can. Repair your walls as needed, and hope your enemies don't bring a trebuchet.


