# 🛠️ How to Enable Wireless Debugging & Bypass Restricted Settings via ADB

This step-by-step guide explains how to enable **Wireless Debugging** on Google TV, Chromecast, or Android TV devices and run ADB terminal commands to enable **EzRemote TV Accessibility Service** in under 2 minutes—no USB cables required.

---

## 📌 Why Is This Required on Google TV / Android 13+?

Android 12/13+ and Google TV enforce a security policy called **Restricted Settings** for sideloaded APKs (apps installed outside the official Google Play Store). This security layer automatically blocks users from toggling on Accessibility Services.

By using **Wireless ADB**, you can grant the required permissions directly to your TV using terminal commands.

---

## 🗺️ Process Overview

```
┌───────────────────────────┐      ┌───────────────────────────┐      ┌───────────────────────────┐
│  1. Enable Developer Mode │ ───► │ 2. Enable Wireless Debug  │ ───► │  3. Pair & Connect ADB    │
│  (Click Build 7 times)    │      │  (Note IP & Ports on TV)  │      │  (adb pair & connect)     │
└───────────────────────────┘      └───────────────────────────┘      └─────────────┬─────────────┘
                                                                                    │
                                                                                    ▼
┌───────────────────────────┐      ┌───────────────────────────┐      ┌───────────────────────────┐
│   6. Remote Control Active│ ◄─── │  5. Launch TV App         │ ◄─── │  4. Grant Permissions     │
│   (Scan QR & Connect)     │      │  (am start command)       │      │  (appops & settings put)  │
└───────────────────────────┘      └───────────────────────────┘      └───────────────────────────┘
```

---

## ⚡ Step-by-Step Instructions

### Phase 1: Enable Developer Options on TV
1. On your Google TV or Chromecast remote, open **Settings** ⚙️ (top-right avatar/gear icon).
2. Navigate to **System** ➔ **About**.
3. Scroll down to **Android TV OS build** (or **Build**).
4. Click the **OK / Center button** on your remote **7 times repeatedly** until a toast notification appears:
   > *"You are now a developer!"*

---

### Phase 2: Enable Wireless Debugging on TV
1. Go back to **Settings** ➔ **System**.
2. Select the newly unlocked **Developer options** menu.
3. Scroll down and turn **ON** **USB debugging**.
4. Scroll down further and turn **ON** **Wireless debugging**.
5. Click directly on **Wireless debugging** to open its detailed status page.

---

### Phase 3: Install ADB on Your Computer / Phone

#### On macOS:
```bash
brew install android-platform-tools
```

#### On Windows:
1. Download the official [Android SDK Platform-Tools for Windows](https://developer.android.com/tools/releases/platform-tools).
2. Extract the ZIP file to `C:\platform-tools`.
3. Open **Command Prompt** (cmd) and navigate to the folder:
   ```cmd
   cd C:\platform-tools
   ```

#### On Linux (Ubuntu/Debian):
```bash
sudo apt-get install android-tools-adb
```

---

### Phase 4: Pair & Connect ADB over Wi-Fi

> [!IMPORTANT]
> Make sure your computer/phone and your Chromecast TV are connected to the **same Wi-Fi network**.

#### Step 4A: Pair Device (One-Time Setup)
1. On your TV screen under **Wireless debugging**, click **"Pair device with pairing code"**.
2. A popup dialog will appear displaying:
   - **IP address & Port**: e.g., `192.168.1.105:`**`44509`**
   - **Wi-Fi pairing code**: e.g., **`533662`**

3. Open Terminal / Command Prompt on your computer and run:
   ```bash
   adb pair <IP-ADDRESS>:<PAIRING-PORT> <PAIRING-CODE>
   ```
   *Example Command:*
   ```bash
   adb pair 192.168.1.105:44509 533662
   ```
   *Expected Output:*
   ```
   Successfully paired to 192.168.1.105:44509 [guid=adb-xxxxxxxx]
   ```

#### Step 4B: Connect ADB
1. Close the pairing popup on your TV screen.
2. Look at the main **Wireless debugging** screen for the main connection port (e.g. `45243`).
3. Connect using terminal:
   ```bash
   adb connect <IP-ADDRESS>:<CONNECT-PORT>
   ```
   *Example Command:*
   ```bash
   adb connect 192.168.1.105:45243
   ```
   *Expected Output:*
   ```
   connected to 192.168.1.105:45243
   ```

---

### Phase 5: Execute 1-Click Permission Commands

Copy and paste the following 3 commands into your terminal to unlock restricted settings and activate **EzRemote TV Accessibility Service**:

#### Command 1: Unlock Restricted Settings (Google TV / Android 13+)
```bash
adb shell appops set com.ezremote.tv ACCESS_RESTRICTED_SETTINGS allow
```

#### Command 2: Enable EzTVControlService Accessibility Service
```bash
adb shell settings put secure enabled_accessibility_services com.ezremote.tv/com.ezremote.tv.service.EzTVControlService
```

#### Command 3: Turn ON Accessibility Master Switch
```bash
adb shell settings put secure accessibility_enabled 1
```

#### Command 4: Verify Activation Status
```bash
adb shell settings get secure enabled_accessibility_services
```
*Expected Output:*
```
com.ezremote.tv/com.ezremote.tv.service.EzTVControlService
```

---

### Phase 6: Launch EzRemote TV App
Launch the EzRemote TV main screen directly on your Chromecast TV:
```bash
adb shell am start -n com.ezremote.tv/.TVHomeActivity
```
*Expected Output:*
```
Starting: Intent { cmp=com.ezremote.tv/.TVHomeActivity }
```

---

## ❓ Troubleshooting & FAQs

### Q1: Terminal says `device offline`
- Run `adb disconnect` to clear stale connections.
- Ensure your TV is awake and the **Wireless debugging** toggle is ON.
- Re-run `adb connect <IP>:<PORT>`.

### Q2: Terminal says `Connection refused`
- The port number under Wireless debugging changes whenever the setting or screen refreshes. Check the current port displayed on your TV screen under **Settings ➔ System ➔ Developer options ➔ Wireless debugging**.

### Q3: `adb pair` failed with `protocol fault`
- Wi-Fi pairing codes expire after 60 seconds. Click **"Pair device with pairing code"** on TV again to generate a fresh pairing port and code.

---

## 📄 License & Support

For issues, feature requests, or updates, visit the official public repository:  
🌐 **[https://github.com/alexsoh/ezremote-tv.free](https://github.com/alexsoh/ezremote-tv.free)**
