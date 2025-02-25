# SANS Institute Black History Month CTF

Tools tried
- `exiftool`
- `file`
- `binwalk`
	- It looked like there may have been something to do with PB and Jelly toward the start of the hexdump in there.
- Decoded the comment in the image metadata into ASCII

- Directory traversal w/ encoding?
- There is nothing really in the page source aside from an indication of an /img/ directory with a spongebob gif inside.

---
## Review
- The `file` command to determine file type + various metadata. e.g. type of executable/binary/etc

## Useful Tools
- Encryption / decryption
	- https://www.dcode.fr/caesar-cipher
	- Cyberchef
- Enumeration
	- Dirbuster
- Passwords
	- John the Ripper
- Binary Analysis
	- Dogbolt: https://dogbolt.org/
	- `strings`
	- `binwalk`

---

Problems:
- nm03 stream
- cm01 base64 encoded ELF binary





