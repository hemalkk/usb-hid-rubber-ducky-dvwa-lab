# Attack Methodology

## Project Aim

The aim of this project is to demonstrate two safe USB HID-assisted attack simulations and explain their defensive significance.

---

## Attack 1: Fake Urgent Update + Safe Recon

### Scenario

A USB HID device is connected to a Linux/Zorin OS lab VM. The device behaves like a keyboard and launches terminal commands automatically.

### Method

1. The HID opens a terminal.
2. It writes a Bash script named `urgent_update.sh`.
3. The script displays a fake urgent security update prompt.
4. A safe background diagnostic process runs.
5. A local report file is created.
6. A fake progress screen is shown to the user.
7. The report is saved locally and copied to a VMware shared folder if available.

### Defensive Purpose

This demonstrates how social engineering and fast HID keystroke injection can hide background activity. It also shows what defenders should monitor.

---

## Attack 2: HID-Assisted DVWA Weaponisation Simulation

### Scenario

After Attack 1, the attacker has basic knowledge of the lab system. Attack 2 safely represents a weaponisation stage against a known local DVWA training target.

### Method

1. The HID opens a terminal.
2. It creates a local lab folder.
3. It creates a harmless marker file.
4. It creates a report explaining the activity.
5. It checks whether DVWA is reachable.
6. It sends one harmless HTTP request.
7. It records defensive mitigations.
8. It copies evidence to the VMware shared folder if available.

### Defensive Purpose

This demonstrates how HID automation can stage activity quickly, while keeping the lab safe and non-destructive.

---

## Why Two Attacks Were Used

The two attacks show different stages:

| Attack | Focus |
|---|---|
| Attack 1 | Social engineering and safe reconnaissance |
| Attack 2 | Safe weaponisation-stage simulation against DVWA |

Together, they show how HID attacks can form part of a wider attack chain while also giving defenders practical indicators to monitor.
