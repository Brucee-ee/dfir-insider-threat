# DFIR — Insider Threat Investigation

CyberDefenders "Insider" challenge — my first solo DFIR project.

## What is this

A digital forensics investigation based on the [CyberDefenders Insider challenge](https://cyberdefenders.org/blueteam-ctf-challenges/64). The scenario is an employee named Karen who starts doing suspicious things on her work machine at a company called TAAUSAI. You're given a forensic disk image (AD1 format) of her Linux workstation and have to figure out what she was up to.

I worked through this over a day, documented everything as I found it, and wrote it up as a proper forensic report rather than a CTF walkthrough.

## Tools

- FTK Imager 8.2.0.59 SP1 — mounting and browsing the AD1 image

## What I found

- A written checklist on her Desktop: *"Gain Bob's Trust — Learn how to hack — Profit"* — clear evidence of premeditated social engineering targeting a named colleague
- Full Mimikatz toolkit extracted to `/root/Desktop/mimikatz/` — credential dumping tool, staged for use against Windows machines on the network
- Metasploit configured with EternalBlue (MS17-010) in `.msf4/history`, with nmap scans and a reverse TCP shell payload pointed at an internal host (10.0.0.101)
- Network recon scripts in `/root/Documents/myfirsthack/`
- Keylogger output (`keys.txt`) capturing keystrokes
- Steganography analysis run on a suspicious image file
- Sudoers file modification via `visudo`
- All high-risk activity occurring between 03:00–05:00, outside normal working hours

## Report

Full forensic report in `/report/` — covers methodology, artefact analysis, incident timeline, indicators of compromise, and recommendations.

Written investigator-style rather than as a CTF walkthrough.

## What I learned

- How to load and browse AD1 images in FTK Imager (not as obvious as it sounds — you have to add it as an evidence item, not open it directly)
- What Mimikatz actually is and why finding it on a Linux machine specifically suggests lateral movement to Windows targets
- How Metasploit stores command history in `.msf4/history` — that file was the most significant find
- How to structure a forensic report properly — artefact, path, timestamp, significance
- The difference between what a CTF answer requires and what an actual investigation report requires

## Notes

I haven't included the original disk image — it belongs to the CyberDefenders challenge. If you want to follow along, download it from the link above (free account required).

---

*Second year Computer Science student at Swansea University, specialising in cybersecurity. Building a portfolio of blue team and DFIR projects ahead of graduate scheme applications.*
