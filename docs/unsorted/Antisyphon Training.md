# Antisyphon Training

# BHIS / Mitre with John Strand
LAB GitHub: https://github.com/KAISERaustin/IntroLabsRemastered/blob/master/IntroClassFiles/Tools/IntroClass/AppLocker/AppLocker.md

Compliance Standards
- CIS → very comprehensive, not beginner friendly
	- cross-maps over to these controls. Intertwined
	- Meeting many major apple pie standards

Atomic Controls
- 11 things

What ACTUALLY works?! What will actually defend a network?
1. Application Allow Listing
2. Password Controls
3. Egress Traffic Analysis
4. UEBA → User and Entity Behavior Analytics
5. Advanced Endpoint Protection
6. Logging
7. Host Firewalls
8. Internet Allow Listing
9. Vulnerability Management
10. Active Directory Hardening
	1. pingcastle
11. Backup and Recovery

Not covering
- Windows
- Linux
- TCP/IP
- Crypto
- Security Models
- CBK
- NIST 800
- DLP (crap that doesn't work)
- *These are covered in **SOC core skills** class*

This approach was informed by asking:
- "What would have stopped us in all of our penetration tests?"
- Tied to MITRE (by the law of everything having to tie to MITRE)

You can't predict what you don't know you don't have.
- Place controls initially, but then circle back to address missing spots

The OSI model is not how computers work:
- IEEE the Internet that wasn't
- TCP/IP is how the internet actually works
- Tell ppl. the OSI model is incorrect

## Compliance and Critical Controls
- FAR too many frameworks
- Conflicting recommendations, they get out of date quickly
- The 12 char password limit is stupid
- Problem: ppl just keep trying to meet the minimum

CIS has excellent mapping and compliance. You can comply automatically by complying to the Critical Controls...
- CIS reasonable cybersecurity guide: recommended

This method is about implementing controls that automatically take care of multiple MITRE TTPs. You're dealing with the CATEGORY of techniques, rather than the specific method.


## Application Allow Listing
- Denylists are a terrible idea. They just don't work. They resonate with the human "ugg and thug"
	- We are not built to recognize RAPIDLY EVOLVING RISKS. We aren't wired for **rapid skepticism**.
	- Enumerating Badness
	- ranum.com/security/computer_security/editorials/dumb

 - Ghostwriting
	 - Lots of blocks of codes that do stuff
	 - metasm (metasploit)
	 - XOR
		- val is 0, they're the same
		- if 1, they're DIFFERENT
		- ***You can do anything you want before that register... because you clear it by XORing it to itself by itself...***
		- This is 1 of the ways polymorphic viruses can evade AVs
	- LOL Bins (living off the land binaries and scripts)
		- https://lolbas-project.github.io/
- Joff Thyer's class on bypassing AV engines
	- https://www.antisyphontraining.com/instructor/joff-thyer/
	- https://www.antisyphontraining.com/course/enterprise-attacker-emulation-and-c2-implant-development-with-joff-thyer/
- Unicorn https://github.com/trustedsec/unicorn
- Where can you execute programs from?
	- ![Pasted image 20250224094731](../assets/images/Pasted%20image%2020250224094731.png)
	- Where SHOULD programs execute?
- Establish custom rules so that certain publishers can execute on your system (as per Windows verified publishers, etc.)
	- Applocker
		- https://www.blackhillsinfosec.com/getting-started-with-applocker/
		- Defult rules are based on Path
			- **These will shutdown like 95% of drive-by download attacks**
		- 