# M5 Cardputer - Arch Linux Setup Guide

**Device:** M5Stack Cardputer (ESP32-based development board)
**OS:** Arch Linux (fresh-tofu)
**Last updated:** 2026-01-30

---

## About M5 Cardputer

The M5Stack Cardputer is a compact ESP32-based IoT development device with a built-in keyboard and display. It's designed for rapid prototyping and development of embedded applications.

### Key Features
- **Chipset:** ESP32 (dual-core Xtensa LX6 microprocessor)
- **Display:** Small built-in screen (varies by model)
- **Input:** Built-in keyboard/card interface
- **Connectivity:** USB-C for flashing and power
- **Wireless:** WiFi and Bluetooth (ESP32 built-in)
- **Form Factor:** Portable, credit-card sized
- **Expansion:** Supports M5Stack unit modules via connector

### Use Cases
- IoT prototyping
- Keyboard-based automation
- Portable development projects
- Learning embedded programming
- WiFi/Bluetooth applications

---

## M5Burner Setup on Arch Linux

### What is M5Burner?

M5Burner is the official firmware flashing tool from M5Stack. It provides a GUI interface to flash pre-built firmware onto M5Stack devices, making it easy to switch between different firmware options (MicroPython, Arduino, UIFlow, etc.).

### Installation

#### 1. Download M5Burner

M5Burner is distributed as a pre-built application. Download the Linux version:

```bash
# Navigate to Downloads
cd ~/Downloads

# Download M5Burner (check M5Stack website for latest version)
# Example URL (verify on https://docs.m5stack.com/en/software/m5burner)
# wget https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/software/M5Burner-v3-beta-linux-x64.zip
```

#### 2. Install to Applications Directory

```bash
# Unzip to Apps directory
unzip M5Burner-v3-beta-linux-x64.zip -d ~/Apps/

# Rename for convenience
cd ~/Apps
mv M5Burner-v3-beta-linux-x64/ M5Burner
```

#### 3. Add User to Required Groups

For USB device access on Arch Linux, add your user to the `uucp` group (for USB serial ports) and `dialout` group (if needed):

```bash
# Add to uucp group (for serial port access)
sudo usermod -aG uucp $USER

# Add to dialout group (alternative for serial devices)
sudo usermod -aG dialout $USER

# Apply group changes immediately
newgrp uucp
```

**Important:** Log out and back in (or run `newgrp`) for group changes to take effect.

#### 4. Verify Installation

```bash
# Navigate to M5Burner directory
cd ~/Apps/M5Burner

# Run M5Burner
./M5Burner

# Or run from bin directory
cd ~/Apps/M5Burner/bin
./m5burner
```

---

## USB Device Access

### Serial Port Permissions

On Arch Linux, USB serial devices (like M5Stack devices) require proper permissions. After adding yourself to the `uucp` group, you can verify access:

```bash
# Check if device is detected
ls -la /dev/ttyUSB* /dev/ttyACM*

# Should see something like:
# crw-rw---- 1 root uucp 188, 0 Jan 30 16:00 /dev/ttyUSB0
```

### udev Rules (Optional)

If you still have permission issues, you can create a udev rule:

```bash
# Create udev rule for M5Stack devices
sudo nano /etc/udev/rules.d/99-m5stack.rules
```

Add this line:
```udev
# M5Stack devices
SUBSYSTEM=="usb", ATTR{idVendor}=="045e", MODE="0666", GROUP="uucp"
```

Then reload udev:
```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```

---

## Flashing Firmware

### Using M5Burner

1. **Connect M5 Cardputer** via USB-C
2. **Open M5Burner:** `~/Apps/M5Burner/M5Burner` or `~/Apps/M5Burner/bin/m5burner`
3. **Select Device:** Choose M5 Cardputer from device list
4. **Select Firmware:** Choose desired firmware (UIFlow, MicroPython, etc.)
5. **Flash:** Click flash button and wait for completion
6. **Connect Device:** After flashing, the device will restart in firmware mode

### Alternative Flashing Methods

#### esptool.py (Command Line)

For advanced users or automation:

```bash
# Install esptool
sudo pacman -S esptool

# Connect device and find port
ls /dev/ttyUSB*

# Flash firmware (example)
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 \
  write_flash 0x1000 firmware.bin
```

#### PlatformIO (with VS Code)

If using PlatformIO for development:

```bash
# Install PlatformIO
pip install platformio

# Or via Arch package
sudo pacman -S platformio

# Flash from VS Code extension or command line
pio run --target upload
```

---

## Development Setup

### MicroPython

```bash
# Install rshell for file transfer
pip install rshell

# Connect and list files
rshell -p /dev/ttyUSB0 --baud 115200

# Or use mpremote
pip install mpremote
mpremote connect /dev/ttyUSB0
mpremote ls
```

### Arduino IDE

```bash
# Install Arduino IDE
sudo pacman -S arduino

# Install ESP32 board support
# Open Arduino IDE -> Tools -> Board -> Boards Manager
# Search "esp32" and install ESP32 by Espressif Systems
```

### PlatformIO (VS Code)

```bash
# Install VS Code extension
code --install-extension platformio.platformio-ide

# Create new project
pio project init --board esp32dev

# Upload
pio run --target upload
```

---

## Troubleshooting

### Device Not Detected

```bash
# Check if device appears in USB list
lsusb | grep -i m5

# Check serial ports
ls -la /dev/ttyUSB* /dev/ttyACM*

# Check kernel messages
dmesg | tail -20
```

### Permission Denied

```bash
# Verify group membership
groups $USER

# If uucp not in groups, add and relogin
sudo usermod -aG uucp $USER
newgrp uucp
```

### Flash Fails

- **Disconnect other USB devices** (especially other ESP32 devices)
- **Try different USB cable** (some cables are power-only)
- **Try different USB port** (avoid USB hubs)
- **Boot into download mode:** Hold boot button while connecting USB

### M5Burner Won't Start

```bash
# Check executable permissions
chmod +x ~/Apps/M5Burner/M5Burner
chmod +x ~/Apps/M5Burner/bin/m5burner

# Run with verbose output
./m5burner --verbose
```

---

## Useful Commands

```bash
# Check USB devices
lsusb

# Check serial ports
ls /dev/ttyUSB* /dev/ttyACM*

# Monitor serial output
sudo picocom -b 115200 /dev/ttyUSB0

# Or use screen
screen /dev/ttyUSB0 115200

# Or use minicom
sudo pacman -S minicom
minicom -D /dev/ttyUSB0 -b 115200
```

---

## Links & Resources

- **M5Stack Official:** https://docs.m5stack.com
- **M5Burner Download:** https://docs.m5stack.com/en/software/m5burner
- **ESP32 Documentation:** https://docs.espressif.com/projects/esp-idf
- **MicroPython:** https://micropython.org
- **PlatformIO:** https://platformio.org

---

## Installation Log (fresh-tofu)

**Date:** 2026-01-30
**System:** Arch Linux (Omarchy)

### Steps Completed:
1. ✅ Downloaded M5Burner-v3-beta-linux-x64.zip
2. ✅ Moved to ~/Apps/M5Burner/
3. ✅ Added user to `dialout` group: `sudo usermod -a -G dialout tofu`
4. ✅ Added user to `uucp` group: `sudo usermod -aG uucp "$USER"`
5. ✅ Applied group changes: `newgrp uucp`
6. ✅ Successfully ran M5Burner from bin directory: `./Apps/M5Burner/bin/m5burner`

### Notes:
- Multiple attempts to run from different paths until correct one found
- `~/Apps/M5Burner/M5Burner` - main executable
- `~/Apps/M5Burner/bin/m5burner` - bin directory executable (works)
- uucp group required for USB serial port access on Arch Linux

---

*Last updated: 2026-01-30 17:25*
