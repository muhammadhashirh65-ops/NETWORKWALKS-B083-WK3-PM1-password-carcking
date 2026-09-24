# Cracking a Password-Protected PDF — Task Walkthrough

This folder contains the step-by-step screenshots for recovering the open
password of a locked PDF file (`My Locked PDF1.pdf`), using **Johnny**
(GUI for John the Ripper), the **OnlineHashCrack PDF Hash Extractor**
tool, and **Adobe Acrobat Reader DC** to confirm the recovered password.

All screenshots have been cleaned — the red highlight boxes and arrows
used for annotation during the walkthrough have been removed, leaving
only the plain application screens.

## Files

### Method 1 — Johnny (John the Ripper GUI) + OnlineHashCrack

| # | File | Description |
|---|------|--------------|
| 1 | `01_johnny_settings_before_path.png` | Johnny opened on the **Settings** tab — no valid John the Ripper executable path has been set yet. |
| 2 | `02_johnny_settings_jtr_detected.png` | The path to `john.exe` (JtR Jumbo 1.9.0, 64-bit) has been browsed to and set; Johnny confirms it detected a valid John the Ripper executable. |
| 3 | `03_onlinehashcrack_pdf_hash_extractor_home.png` | The OnlineHashCrack **PDF Hash Extractor** tool page, used to convert the locked PDF into a crackable hash (equivalent to `pdf2john`). |
| 4 | `04_onlinehashcrack_pdf_uploaded.png` | `My Locked PDF1.pdf` selected and ready to be uploaded to the extractor. |
| 5 | `05_onlinehashcrack_hash_output_copy.png` | The extracted `$pdf$...` hash shown in the Output box, being copied to the clipboard. |
| 6 | `06_downloaded_pdf_and_hash_file.png` | Local folder showing the original locked PDF alongside the saved `hash1.txt` file containing the extracted hash. |
| 7 | `07_adobe_acrobat_password_prompt.png` | Adobe Acrobat Reader DC prompting for the Document Open Password, used to verify the password recovered by John the Ripper. |
| 8 | `08_flag1_captured_congratulations.png` | The unlocked PDF opens successfully, confirming the recovered password and displaying the "Congratulations! You have captured your 1st flag." message. |

### Method 2 — Networkwalks browser-based Hash Calculator + Password Cracker

| # | File | Description |
|---|------|--------------|
| 9 | `09_networkwalks_hash_calculator_home.png` | The Networkwalks **Hash Calculator** tool (networkwalks.com/hash-calculator), which can generate MD5/SHA hashes or extract a crackable hash directly from a password-protected PDF, entirely in-browser. |
| 10 | `10_networkwalks_pdf_hash_extracted.png` | `My-Locked-PDF1.pdf` uploaded to the **PDF** tab; the tool detects it is encrypted and extracts the same `$pdf$...` hash (pdf2john/hashcat compatible format), with Copy/Download options. |
| 11 | `11_networkwalks_password_cracker_lab.png` | The Networkwalks **Password Cracker — Dictionary Attack Lab**, a browser demo that hashes each word in a wordlist and matches it against the pasted PDF hash, illustrating the same idea John the Ripper uses. |
| 12 | `12_networkwalks_password_cracked_result.png` | The dictionary attack in progress and completed — the wordlist is tried word by word until a match is found, recovering the password `password1`. |
| 13 | `13_flag1_captured_congratulations_v2.png` | The PDF opened with the recovered password, again showing the "Congratulations! You have captured your 1st flag." confirmation. |

## Workflow Summary

**Method 1 (desktop tools):**
1. **Configure Johnny** — Point Johnny to a working John the Ripper
   (Jumbo) executable under *Settings* so it can drive attacks (images 1–2).
2. **Extract the hash** — Upload the locked PDF to the OnlineHashCrack
   PDF Hash Extractor to generate a `pdf2john`-style hash (images 3–4),
   then copy the resulting hash string (image 5).
3. **Save the hash** — Store the copied hash in a text file
   (`hash1.txt`) next to the PDF (image 6).
4. **Crack the hash** — Run John the Ripper / Johnny against
   `hash1.txt` (e.g. with a wordlist attack) to recover the PDF's
   open password.
5. **Verify** — Open the PDF in Adobe Acrobat Reader DC, enter the
   recovered password at the prompt (image 7), and confirm successful
   access via the "flag captured" confirmation page (image 8).

**Method 2 (browser-only tools, no local install):**
1. **Extract the hash** — Use the Networkwalks Hash Calculator's PDF
   tab to upload the locked PDF and extract the same `$pdf$...` hash
   directly in the browser (images 9–10).
2. **Crack the hash** — Paste the hash into the Networkwalks Password
   Cracker (Dictionary Attack Lab), run the built-in 100-word wordlist
   attack, and recover the password `password1` (images 11–12).
3. **Verify** — Open the PDF with the recovered password and confirm
   the "flag captured" page (image 13).

Both methods recover the **same password** (`password1`) for the
**same PDF**, demonstrating that a local John the Ripper attack and a
browser-based dictionary attack are conceptually identical — hashing
each candidate password and comparing it to the target hash.

## Notes

- Red annotation boxes/arrows originally used to highlight UI elements
  in screenshots 1–8 have been digitally removed for a clean,
  presentation-ready set of images.
- Screenshots 9–13 required no editing — their pink/magenta colour
  scheme is the Networkwalks site's own theme, not annotation markup.
- File names are numbered to reflect the order of the walkthrough.
