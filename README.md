# NetworkWalks Week 3 — Password Cracking (JTR & NetworkWalks Tools)

**Password Cracking (W3-PM1) + Password Cracking with NetworkWalks Tools (W3-PM2) | NetworkWalks Week 3 | B084C**

## Overview
This repo documents Week 3 of the NetworkWalks Cybersecurity internship: recovering the password of a protected PDF file (`My Locked PDF1.pdf`) using two different approaches.

- **PM1** — John the Ripper (John + Johnny GUI) on Windows
- **PM2** — NetworkWalks' own free online tools (Hash Calculator + Password Cracker)

Both tasks target the same locked PDF, so the repo compares a local offline tool against a browser-based online tool for the same job.

## Tools Used
| Task | Tool | Type |
|------|------|------|
| PM1 | John the Ripper (John) | CLI password cracker |
| PM1 | Johnny | GUI front-end for John |
| PM2 | NetworkWalks Hash Calculator | Online hash extractor |
| PM2 | NetworkWalks Password Cracker | Online dictionary attacker |

## Methodology

### PM1 — John the Ripper / Johnny
1. Installed John the Ripper (jumbo) and Johnny GUI on Windows.
2. Extracted the PDF's crackable hash (`$pdf$...` format, pdf2john/hashcat-compatible).
3. Saved the hash into a text file.
4. Opened the hash file in Johnny, pointed Johnny to `john.exe`, and ran **Start new attack**.
5. Johnny recovered the password and displayed it in the Passwords tab (see screenshot 1).
6. Entered the recovered password to unlock the PDF (see screenshot 3).

### PM2 — NetworkWalks Hash Calculator + Password Cracker
1. Uploaded the same locked PDF to the **Hash Calculator** (`networkwalks.com/hash-calculator`) to extract the `$pdf$...` hash — done entirely in-browser, no install needed (see screenshot 2).
2. Copied the hash and pasted it into the **Password Cracker** (`networkwalks.com/password-cracker`).
3. Ran the dictionary attack against the built-in wordlist.
4. Tool matched and displayed the same cracked password.
5. Verified by unlocking the PDF with the recovered password.

## Result
- **Target file:** `My Locked PDF1.pdf`
- **Hash format:** `$pdf$4*4*128*-1028*1*16*...` (pdf2john/hashcat-compatible)
- **Recovered password:** `good-luck`
- Confirmed by unlocking the PDF, which revealed the captured flag: `nw{cybersecurity_flag_captured_2608}`

## Key Takeaway
Even a password that looks slightly less generic than "password1" — like `good-luck` — is still a dictionary word pattern and falls instantly to a basic dictionary attack, whether run locally with John the Ripper or through a lightweight browser-based tool. This reinforces why strong, unique, non-dictionary passwords (length + mixed character types + randomness) are essential — predictable words offer no real protection even for "locked" files.

## Screenshots
| # | File | Description |
|---|------|-------------|
| 1 | [`screenshots/01-johnny-password-cracked.png`](./screenshots/01-johnny-password-cracked.png) | Johnny GUI showing the PDF hash cracked — password `good-luck` recovered (100%, 1/1 cracked) |
| 2 | [`screenshots/02-pdf-hash-extracted.png`](./screenshots/02-pdf-hash-extracted.png) | Hash extracted from `My Locked PDF1.pdf` in `$pdf$...` format |
| 3 | [`screenshots/03-pdf-unlocked-password-entered.png`](./screenshots/03-pdf-unlocked-password-entered.png) | Entering the recovered password to unlock the PDF |
| 4 | [`screenshots/04-flag-captured.png`](./screenshots/04-flag-captured.png) | Flag captured inside the unlocked PDF: `nw{cybersecurity_flag_captured_2608}` |

## Credits
- Lab & tools by [NetworkWalks Academy](https://networkwalks.com)
- Instructor: Waqas Karim CCIE
- Completed as part of the NetworkWalks Cybersecurity Internship (Batch B084C), Week 3
