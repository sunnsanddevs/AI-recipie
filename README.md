# AI-recipie
this is my own collection of AI recipies for community good
# Pritz AI Recipe — Faster, Customizable Android / Google TV
##thanks to cleanyourtv and everyones contribution https://github.com/Gathin23/cleanyourtv/tree/main 
A step-by-step guide and prompt sequence to debloat any Android TV / Google TV, replace the laggy stock launcher with a clean, lightweight Apple TV-style home screen, add RAM & Task management, and enable ad blocking using Bob.

---

## Prerequisites (On the TV)

1. **Enable Developer Options**:
   - Go to **Settings → System → About**.
   - Scroll to **Android TV OS build** (or **Build**) and press **OK 7 times** until you see *"You are now a developer!"*.
2. **Enable Network / USB Debugging**:
   - Go to **Settings → System → Developer options**.
   - Turn **USB debugging** **ON**.
   - Turn **Wireless debugging** (or **Network debugging**) **ON** if present.
3. **Connect to Wi-Fi**:
   - Ensure the TV and your computer running Bob are connected to the same Wi-Fi network.

---

## The Prompt Sequence (Copy & Paste to Bob)

### Step 1: Connect, Backup & Initial Debloat
Copy and send this prompt to Bob:

```text
I want to debloat my Android TV and replace its launcher with a clean Apple TV style home screen. My TV model is: <YOUR_TV_MODEL_HERE, e.g. Acer R4 55 inch TV>. Work on the real device, step by step, and verify everything you do with screenshots pulled from the TV. Ask me before anything that depends on my preferences. Where these steps name a file under tools/, docs/ or examples/ that is not in your working folder, clone https://github.com/Gathin23/cleanyourtv and work from there.

1. Connect to the TV over ADB (port 5555 or Wireless debugging).
2. Take a baseline backup of packages, settings, and an initial screenshot.
3. Ask me my preferences for USB ports, streaming apps, Private DNS (AdGuard), and dock apps.
4. Disable bloatware, manufacturer telemetry, and unselected streaming apps in small batches using pm disable-user --user 0. Never uninstall packages.
```

---

### Step 2: Add RAM & Task Manager with Clear RAM
Once the initial setup is complete, send:

```text
Add UI improvements to the launcher:
1. Add a RAM & Task Manager that displays live Used RAM, Total RAM, and Free RAM percentage.
2. Show a list of active background apps with their memory usage in MB and individual Stop buttons.
3. Add a one-click "Clear RAM" button to optimize memory and free up background tasks.
4. Add a Wallpaper selection option directly in the launcher settings and quick settings.
```

---

### Step 3: Add Top-Bar Controls & Scenic Themes
Send:

```text
1. Add a frosted circular Home Icon button on the top bar of the main screen so all launcher controls (RAM manager, wallpapers, columns, dock settings) are accessible with one click.
2. Add 20 picturesque themes/wallpapers of nature, forests, ocean, sea, and beach that can be chosen directly on the TV.
```

---

### Step 4: Check HDMI ARC / Audio & Finalize
Send:

```text
1. Check if HDMI ARC and CEC volume control are active and connected to my soundbar/audio system. If not, enable them.
2. Provide a restore script, debloat list, and instructions on how to re-enable any app or revert changes.
```

---

## What Gets Configured

| Feature | What It Does |
| :--- | :--- |
| **Debloat Engine** | Disables background analytics, telemetry, demo apps, and unneeded preinstalled bloatware without removing system files. |
| **Apple TV UI** | Fast, hardware-accelerated grid with pitch black background, ambient dock glow, and customizable dock slots. |
| **RAM & Task Manager** | Real-time memory gauge, active task monitor, and one-click RAM cleaner. |
| **Top-Bar Home Button** | Direct access to all launcher settings, task management, and themes from the home screen. |
| **20 Scenic Themes** | High-definition wallpapers for forests, beaches, oceans, and mountains bundled directly into the launcher. |
| **AdGuard Private DNS** | Blocks system telemetry and third-party app ads automatically. |

---

## Safe Undo / How to Restore

- **Re-enable any individual app**:
  ```bash
  tools/venv/bin/python tools/tv.py 'pm enable --user 0 <package_name>'
  ```
- **Run Full Factory Restore**:
  ```bash
  ./backup/restore_acer_r4.sh
  ```
- **Revert DNS to Default**:
  ```bash
  tools/venv/bin/python tools/tv.py 'settings put global private_dns_mode opportunistic'
  ```
