# Installation Guide – Xiaomi 12T (plato)

> [!WARNING]
> You are solely responsible for your device and actions. Neither the ROM maintainer nor the author of this guide is responsible for any damage, data loss, or issues that may occur during installation.

---

## 📦 Requirements

Before starting, make sure you have the following:

- Latest ROM package for **Xiaomi 12T (plato)**
- [Android Platform Tools (ADB & Fastboot)](https://developer.android.com/tools/releases/platform-tools)
- Optional: GApps package (if required)
- [Engineering firmware preloader](https://pixeldrain.com/u/6eYXU83J)

Additionally:

- Bootloader must be **unlocked**

> [!IMPORTANT]
> Flashing the engineering firmware preloader is strongly recommended. It provides an additional recovery path and may allow restoring stock firmware without requiring service center assistance if something goes wrong.

---

## ⚙️ Step 1: Enter Fastboot mode

Power off the device, then hold:

**Volume Down + Power**

until the Fastboot screen appears.

---

## 🔧 Step 2: Flash preloader

Flash the preloader:

```bash
fastboot flash preloader1 preloader_plato.bin
fastboot flash preloader2 preloader_plato.bin
```

If the commands fail, use the alternative partition names:
```bash
fastboot flash preloader_raw_a preloader_plato.bin
fastboot flash preloader_raw_b preloader_plato.bin
```
## 📲 Step 3: Flash boot images
```bash
fastboot flash boot boot.img
fastboot flash vendor_boot vendor_boot.img
fastboot reboot recovery
```
After reboot, the device should boot into recovery mode.

## 🧹 Step 4: Format data

Inside recovery:

Select Factory reset / Wipe data
Confirm the operation

> [!IMPORTANT]
> Formatting data is required when installing the ROM. 

## 📥 Step 5: Install ROM

From your PC:

```bash
adb sideload <ROM>.zip
```

If Recovery prompts for a reboot at approximately **47%**, confirm it.

## Step 5: Flash GApps (Optional)

If you require Google services, flash the GApps package after installing the ROM:

```bash
adb sideload <gapps-package>.zip
```

No additional packages are required.

## 🔄 Step 7: Reboot system

Once installation is complete:

```bash
Reboot System
```

First boot may take longer than usual.

## 📌 Notes
- Steps may vary depending on ROM build
- Always follow release-specific instructions if provided
- Keep a backup of important data before flashing
