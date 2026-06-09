# Detection and Mitigation

## Detection Indicators

Security teams can look for the following indicators:

### USB / Device Indicators

- New USB HID keyboard detected.
- Unknown vendor/product ID.
- USB device connected shortly before suspicious terminal activity.
- HID device connected to an unattended workstation.

### Endpoint Indicators

- Terminal launched unexpectedly.
- Bash script created in the home directory.
- Commands typed faster than normal human speed.
- Use of commands such as `whoami`, `hostname`, `ip addr`, `ip route`, `ss`, `lsusb`, or `curl`.
- Creation of files such as:
  - `system_update_log.txt`
  - `attack2_dvwa_weaponisation_report.txt`
  - `simulated_dvwa_payload_marker.txt`

### User Behaviour Indicators

- Fake update prompt appears unexpectedly.
- User asked to type confirmation into an unknown terminal prompt.
- Progress messages appear without a real software update tool.

### Network Indicators

- Unexpected request to DVWA or local web application.
- Unexpected `curl` activity from a normal user workstation.

---

## Mitigation Strategies

| Risk | Mitigation |
|---|---|
| Unknown HID devices | USB allow-listing and device control |
| Unattended systems | Screen lock policy and physical security |
| Rapid command execution | EDR monitoring and command-line logging |
| User deception | Security awareness training |
| High privilege misuse | Least privilege accounts |
| Vulnerable local apps | Isolate DVWA and training apps from production |
| Weak visibility | Centralised logging and alerting |

---

## Recommended Controls

1. Block or approve-list unknown USB HID devices.
2. Use endpoint monitoring to detect rapid terminal launch.
3. Log process creation events.
4. Monitor shell commands and suspicious script creation.
5. Disable unnecessary USB ports on sensitive systems.
6. Train users to report unexpected update prompts.
7. Keep vulnerable applications such as DVWA isolated.
8. Apply least privilege to all users.
9. Use screen lock policies for unattended machines.
10. Review physical security controls.
