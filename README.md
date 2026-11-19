# Week 3 | Project Module 2 — Password Cracking with Networkwalks Tools

## Overview
This project demonstrates password recovery on password-protected PDF files using Networkwalks' own web-based **Hash Calculator** and **Password Cracker** tools, as part of a Networkwalks Cybersecurity internship module. Unlike Module 1 (which used John the Ripper/Johnny locally), this module relies entirely on browser-based tools that replicate the `pdf2john` + dictionary-attack workflow.

## Tools Used
- **Networkwalks Hash Calculator** — `https://networkwalks.com/hash-calculator/`
  Extracts a crackable `$pdf$...` hash (pdf2john / hashcat compatible format) directly from an encrypted PDF, parsed locally in-browser.
- **Networkwalks Password Cracker** — `https://networkwalks.com/password-cracker/`
  A dictionary-attack lab that hashes every word in a wordlist and matches it against the PDF password hash (same concept as John the Ripper).

## Methodology (repeated for each PDF)
1. **Download PDF** — Downloaded the encrypted PDF file to the laptop.
2. **Extract Hash** — Opened the Networkwalks Hash Calculator, uploaded the locked PDF under the **PDF** tab. The tool parsed it locally and generated a crackable hash starting with `$pdf$...`.
3. **Copy Hash** — Copied the complete hash value (ensuring no part was cut off).
4. **Open Password Cracker** — Opened the Networkwalks Password Cracker tool.
5. **Paste Hash** — Pasted the full `$pdf$...` hash into the **PDF HASH** input field.
6. **Run Attack** — Selected the wordlist (built-in list of 100 passwords, or an uploaded custom wordlist when the built-in list failed) and clicked **Start Cracking**.
7. **Retrieve Password** — The tool tried passwords one by one until it found a match, displaying **"PASSWORD CRACKED SUCCESSFULLY"** along with the plaintext password.
8. **Unlock PDF** — Opened the locked PDF and entered the cracked password to unlock it and capture the flag.

## Results

| PDF File | Cracked Password | Flag Captured |
|---|---|---|
| My Locked PDF1.pdf | `good-luck` | `nw{cybersecurity_flag_captured_2608}` |
| My Locked PDF2.pdf | `password1` | `nw{networkwalks_persistence_jtr_270521}` |
| My Locked PDF3.pdf | `1qaz2wsx` | `nw{networkwalks_flag_260821_1}` |

All three encrypted PDFs were successfully cracked and their flags retrieved using only browser-based Networkwalks tools — no software installation required.

## Key Learnings
- How a password-protected PDF's hash can be extracted and cracked entirely through browser-based tools, without installing CLI software like John the Ripper.
- Reinforced understanding of the **dictionary attack** concept — testing a list of known/common passwords against a hash until a match is found.
- Observed that when a built-in/small wordlist fails to crack a password, switching to a larger or custom wordlist increases the chance of success.
- Compared to Module 1 (JTR/Johnny), this module highlighted how the same underlying cracking logic can be delivered as a lightweight, no-install web tool — useful for quick checks without local setup.

## Status
✅ **Project Module 2 — Completed**
