# Password Cracking Labs: John the Ripper & Networkwalks Tools

Hands-on labs from the Networkwalks Cybersecurity & Ethical Hacking course (Week 3). The goal was to recover the password of an intentionally locked PDF and understand why weak passwords fail.

> **Disclaimer:** All work was done on a lab file provided for training. Don't run these techniques against files or systems you don't own or have permission to test.

## Overview

| Module | Focus | Tools |
|--------|-------|-------|
| 1 | Cracking a PDF password with JtR | John the Ripper (jumbo 1.9.0), Johnny GUI, OnlineHashCrack PDF Hash Extractor |
| 2 | Cracking the same PDF in the browser | Networkwalks Hash Calculator, Networkwalks Password Cracker |

Across both modules, I recovered 4 passwords in total.

## Environment

- Windows PC (both labs can also run on Kali Linux)
- John the Ripper jumbo 1.9.0 (Windows 64-bit build)
- Johnny 2.2 (GUI front end for John)
- Any modern web browser for the Networkwalks tools

## Methodology

### Module 1: John the Ripper and Johnny
1. Downloaded John the Ripper and Johnny, and pointed Johnny at `john.exe`
2. Uploaded the locked PDF to the OnlineHashCrack PDF Hash Extractor (pdf2john-based) to get the hash
3. Saved the `$pdf$...` hash to `hash1.txt` (removing any stray `b'` prefix)
4. Loaded the file in Johnny and ran **Start new attack**
5. Used the recovered password to open the PDF

### Module 2: Networkwalks tools
1. Uploaded the PDF to the Networkwalks Hash Calculator (parsed locally in the browser)
2. Copied the full `$pdf$` hash
3. Pasted it into the Networkwalks Password Cracker and ran a dictionary attack with the built-in 100-word list
4. Opened the PDF with the cracked password

## Hash details

- Format: `$pdf$` (pdf2john / hashcat compatible)
- PDF encryption: Revision 4, Version 4, 128-bit key
- The full hash is intentionally not included in this repo

## Key takeaways

- A protected file stores a **hash** of the password, not the password itself.
- Hashing is one-way. Attackers don't reverse it; they guess candidates and compare.
- **Dictionary attacks** are fast against common, predictable passwords, including a common word with a number added.
- Length and randomness matter more than small substitutions.
- Defensive habits that follow: password managers, unique passwords, long passphrases, and MFA.

## Acknowledgements

Labs by [Networkwalks](https://www.networkwalks.com).

## Tools

[John the Ripper](https://www.openwall.com/john/) · [Johnny](https://openwall.info/wiki/john/johnny) · [Networkwalks Hash Calculator](https://networkwalks.com/hash-calculator/) · [Networkwalks Password Cracker](https://networkwalks.com/password-cracker/)
