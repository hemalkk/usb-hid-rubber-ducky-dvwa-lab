# Setup Guide

## 1. Required Equipment

- Raspberry Pi Pico
- USB-A to micro-USB cable
- Dupont cable
- A lab VM such as Zorin OS or Ubuntu
- DVWA installed locally for Attack 2
- CircuitPython installed on the Pico
- DuckyScript interpreter for Pico-Ducky

## 2. Configure Raspberry Pi Pico as HID

### Step 1: Install CircuitPython

1. Download the CircuitPython `.uf2` file for Raspberry Pi Pico.
2. Hold the **BOOTSEL** button while plugging the Pico into the computer.
3. The device should appear as `RPI-RP2`.
4. Copy the `.uf2` file to the root of `RPI-RP2`.
5. The device will reboot and appear as `CIRCUITPY`.

### Step 2: Add HID Library

1. Download the Adafruit CircuitPython library bundle.
2. Extract the bundle on your computer.
3. Open the extracted `lib` folder.
4. Copy the full `adafruit_hid` folder into the `lib` folder on `CIRCUITPY`.

### Step 3: Add DuckyScript Interpreter

1. Copy the Pico-Ducky / `duckyinpython.py` interpreter code into `code.py`.
2. Save `code.py` in the root of the `CIRCUITPY` drive.
3. The interpreter will look for a file named `payload.dd`.

## 3. Setup Mode

Before editing payloads, put the Pico into setup mode.

Use the Dupont cable to connect:

```text
GP0 / Pin 1  ->  GND / Pin 3
```

This prevents the payload from running immediately when the device is plugged in.

## 4. Add a Payload

1. Choose one payload from the `payloads/` folder.
2. Copy its content into a file named:

```text
payload.dd
```

3. Place `payload.dd` in the root of the `CIRCUITPY` drive.
4. Safely eject the device.
5. Remove the setup-mode jumper only when ready to test in the authorised VM.

## 5. Attack 1 Test

Use:

```text
payloads/attack_01_fake_update_safe_recon.ducky
```

Expected output on the VM:

```text
~/system_update_log.txt
```

If VMware shared folder is available, it may also copy to:

```text
/mnt/hgfs/Desktop/system_update_log_from_zorin.txt
```

## 6. Attack 2 Test

Use:

```text
payloads/attack_02_dvwa_weaponisation_simulation.ducky
```

Expected output on the VM:

```text
~/ducky_attack2_dvwa_weaponisation/attack2_dvwa_weaponisation_report.txt
~/ducky_attack2_dvwa_weaponisation/simulated_dvwa_payload_marker.txt
```

If VMware shared folder is available, files may also copy to:

```text
/mnt/hgfs/Desktop/
```

## 7. Evidence to Capture

Save screenshots in:

```text
evidence/screenshots/
```

Recommended screenshots:

- Pico setup mode
- CIRCUITPY drive
- Payload file placement
- Attack 1 terminal execution
- Attack 1 generated report
- Attack 2 terminal execution
- Attack 2 generated report
- DVWA reachability evidence
- Mitigation/detection notes
