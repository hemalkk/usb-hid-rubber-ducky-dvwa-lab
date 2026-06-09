# USB HID / Rubber Ducky Security Simulation Lab

## Project Overview

This repository contains a safe, portfolio-ready USB HID / Rubber Ducky-style lab project.  
The project demonstrates two controlled attacks using DuckyScript against a local Linux/Zorin OS virtual machine:

1. **Attack 1:** Fake urgent update + safe background reconnaissance  
2. **Attack 2:** HID-assisted DVWA weaponisation simulation

The aim is to show how USB Human Interface Device (HID) attacks can automate user input, why this behaviour is risky, and how organisations can detect and mitigate it.

This project is designed for an authorised educational lab only. It does **not** include malware, credential theft, persistence, destructive commands, SQL injection, reverse shells, or real exfiltration.

---

## Repository Structure

```text
usb-hid-rubber-ducky-dvwa-lab/
│
├── README.md
├── attack_01_fake_update_safe_recon.ducky
├── attack_02_dvwa_weaponisation_simulation.ducky
├── ethical-notice.md
├── setup-guide.md
├── attack-methodology.md
├── detection-and-mitigation.md
├──references.md
```

---

## Lab Environment

| Component | Description |
|---|---|
| HID Device | Raspberry Pi Pico / USB Rubber Ducky-style HID |
| Firmware | CircuitPython with DuckyScript interpreter |
| Target VM | Zorin OS / Ubuntu-based Linux VM |
| Web App | DVWA running locally |
| Main Languages | DuckyScript and Bash |
| Purpose | Educational security simulation and defensive analysis |

---

## Attack 1: Fake Urgent Update + Safe Recon

### Aim

This attack demonstrates a social-engineering style fake update screen while a safe background script collects basic diagnostic information from the lab VM.

### What It Does

The payload:

- Opens a terminal.
- Creates a fake urgent update script.
- Displays a fake update message and progress screen.
- Creates a local diagnostic report.
- Collects basic system information only:
  - Current user
  - Hostname
  - OS information
  - Kernel information
  - Network addresses
  - Routes
  - Listening ports
  - SSH status
  - Firewall status
  - USB device list
- Saves the report locally.
- Copies the report to a VMware shared folder if available.

### Safety Limits

This attack does **not** collect:

- Passwords
- Browser data
- SSH keys
- Private files
- Tokens
- Cookies
- Credentials

---

## Attack 2: HID-Assisted DVWA Weaponisation Simulation

### Aim

This attack demonstrates how a HID device could stage a web-attack preparation step after reconnaissance, but in a safe way.

### What It Does

The payload:

- Opens a terminal.
- Creates a local lab folder.
- Creates a harmless simulated payload marker file.
- Creates a report explaining the activity.
- Maps the activity to MITRE ATT&CK.
- Checks whether DVWA is reachable at `http://127.0.0.1/dvwa/`.
- Sends a harmless HTTP request to DVWA.
- Records mitigation recommendations.
- Copies the report and marker file to a VMware shared folder if available.

### Safety Limits

This attack does **not** perform:

- SQL injection
- Command injection
- Credential theft
- Malware execution
- Persistence
- Reverse shell
- Destructive activity
- Real exfiltration

---

## MITRE ATT&CK Mapping

| Technique | Explanation |
|---|---|
| T1200 - Hardware Additions | Raspberry Pi Pico / USB HID device behaves like a keyboard |
| T1059.004 - Unix Shell | Commands are executed through a Linux shell |

---

## Detection Ideas

Possible indicators of suspicious HID activity include:

- New or unknown USB HID device connection.
- Terminal opens unexpectedly.
- Very fast automated keystrokes.
- Shell script created immediately after USB insertion.
- Suspicious fake update prompt.
- Unexpected `curl` request to a local web application.
- New report or marker files created without normal user action.
- Repeated process chain involving terminal, bash, and curl.

---

## Mitigation Strategies

Organisations can reduce risk by applying:

- USB device allow-listing.
- Blocking unknown HID devices.
- Endpoint Detection and Response monitoring.
- Alerts for rapid terminal launch and automated keystrokes.
- Least privilege user accounts.
- Workstation lock policies.
- User awareness training.
- Isolation of vulnerable lab applications such as DVWA.
- Physical security controls for unattended machines.

---

---

## Disclaimer

This repository is for authorised educational use only.  
Do not run HID payloads on systems you do not own or do not have permission to test.
