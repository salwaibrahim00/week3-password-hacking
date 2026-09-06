# Week 3 — Password Cracking with JTR (John the Ripper)

Cybersecurity coursework project (Networkwalks Academy — Cyber IT Diploma) covering password recovery from encrypted PDF files using John the Ripper (JTR) and its GUI front-end, Johnny.

## ⚠️ Disclaimer

All password-cracking activity in this repo was performed only against files explicitly provided for this course exercise. This content is for educational purposes only — never attempt to crack passwords on files or systems you do not own or have explicit permission to test.

## Objective

Recover the password of three encrypted PDF files using:
- **John the Ripper (JTR)** — command-line password cracking tool, pre-installed on Kali Linux
- **Johnny** — the graphical front-end for JTR
- **pdf2john** — extracts a crackable hash from an encrypted PDF (bundled with JTR)
- **Networkwalks Hash Calculator** — a browser-based alternative that extracts the same `$pdf$` hash format entirely client-side (no file upload — the PDF is parsed locally in-browser)

## Method

1. Extracted the password hash from each encrypted PDF using `pdf2john` (native Kali install) or the Networkwalks Hash Calculator (client-side, no upload)
2. Loaded each hash into **Johnny**
3. Ran a dictionary/wordlist attack until a match was found
4. Used the recovered password to unlock the original PDF and confirm the flag inside

## Results

| File | Hash Extraction Method | Password Cracked | Flag Captured |
|---|---|---|---|
| My Locked PDF1.pdf | `pdf2john` (local) | `good-luck` | `nw{networkwalks_flag1_jtr_270521_1}` |
| My Locked PDF2.pdf | `pdf2john` (local) | `1qaz2wsx` | *(captured — see screenshot)* |
| My Locked PDF3.pdf | Networkwalks Hash Calculator (client-side) | `password1` | `nw{networkwalks_flag_260821_1}` |

## Repo Structure

- `README.md`
- `screenshots/` — screenshots documenting each cracking step and captured flag

## Key Takeaways

- `pdf2john` converts a PDF's encryption metadata into a hash format that John the Ripper can attack — this only works because PDF encryption checks a password against a derived key, which can be tested offline once the hash is extracted
- Weak, common passwords (`good-luck`, `password1`, `1qaz2wsx`) are cracked almost instantly against a small dictionary — reinforcing why password complexity and length matter far more than obscurity
- Extracting hashes locally (via `pdf2john` or a client-side tool) avoids uploading potentially sensitive files to third-party servers — good practice even for low-stakes lab files

## Tools Used

`John the Ripper` · `Johnny` · `pdf2john` · Networkwalks Hash Calculator

## Author

Salwa — [github.com/salwaibrahim00](https://github.com/salwaibrahim00)
