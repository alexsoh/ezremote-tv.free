# 📺 EzRemote TV - Turn Any Browser Into an Android TV Remote

[![Release](https://img.shields.io/badge/release-v1.0-6366f1.svg?style=for-the-badge&logo=android)](releases/ezremote-tv-v1.0.apk)
[![Platform](https://img.shields.io/badge/platform-Android%20TV%20%7C%20Google%20TV-10b981.svg?style=for-the-badge&logo=android)](https://www.android.com/tv/)
[![License](https://img.shields.io/badge/license-MIT-8b5cf6.svg?style=for-the-badge)](#license)
[![Zero Install Client](https://img.shields.io/badge/client-Web%20Browser-3b82f6.svg?style=for-the-badge&logo=googlechrome)](https://github.com/alexsoh/ezremote-tv.free)

> **No mobile app required!** Install **EzRemote TV** on your Android TV or Google TV, open any web browser on your smartphone, tablet, or PC, scan the QR code, and take total control.

---

## ⚡ Quick Download

📥 **[Download EzRemote TV v1.0 APK (Direct Link)](ezremote-tv-v1.0.apk)**  
*Compatible with Android 7.0+ (API 24+) Android TV & Google TV devices.*

---

## ✨ Features at a Glance

### 📱 Zero-Install Mobile Control
No need to download mobile apps from the Play Store or App Store. Simply scan the **QR Code** on your TV screen with your phone camera to instantly launch the web remote interface.

### 🎯 Glowing D-Pad & Trackpad Modes
- **D-Pad Ring**: Intuitive directional controls (Up, Down, Left, Right, OK/Select) with responsive visual glow and haptic vibration.
- **Gesture Touchpad**: Drag to navigate mouse pointers, tap to select, and swipe through long content cards easily.

### 🚀 1-Click App Launcher Shelf
View all installed Android TV apps (YouTube, Netflix, Prime Video, Disney+, Spotify, etc.) directly on your phone screen. Tap any app card to launch it instantly on your TV.

### ⌨️ Virtual Text Keyboard
Tired of typing letter-by-letter using a TV remote on-screen keyboard? Type directly on your phone keyboard or paste long search strings into YouTube, Netflix, or web browsers.

### 🔒 Local PIN Security & Auto-Reconnect
Protects your TV from unauthorized network access. On initial connection, enter the 4-digit PIN generated on your TV screen. Future connections auto-reconnect silently in under 100ms!

---

## 🛠️ Quick Setup Guide (3 Steps)

### Step 1: Install the TV App
1. Download [ezremote-tv-v1.0.apk](ezremote-tv-v1.0.apk) to your Android TV or Google TV device.
2. Install and launch **EzRemote TV** from your TV home screen.

### Step 2: Enable Control Service (One-Time)
- Click **"Enable in Settings"** on the TV screen.
- Toggle **EzTVControlService** to **ON** under Accessibility Settings.

> [!WARNING]
> **Google TV / Android 13+ Notice (Toggle Turns Off Automatically?)**
> Android 13+ and Google TV OS restrict Accessibility Services for sideloaded APKs by default. If the accessibility toggle automatically flips back OFF when clicked:
> 1. Go to TV **Settings** -> **Apps** -> **See all apps** -> **EzRemote TV**.
> 2. Scroll to the bottom (or click top-right 3 dots) and select **"Allow restricted settings"**.
> 3. Enter your TV PIN/password if prompted.
> 4. Go back to **Settings** -> **System** -> **Accessibility** -> **EzTVControlService** and toggle it **ON**.

### Step 3: Scan & Connect
- Make sure your smartphone or PC is connected to the same Wi-Fi network.
- Scan the on-screen **QR Code** or type `http://<TV-IP>:8080` in your web browser.
- Enter the 4-digit PIN shown on the TV to connect.

---

## ⚡ Zero-Click ADB Command Bypass (Optional)

If you have ADB enabled on your TV or Android TV emulator:
```bash
adb shell settings put secure enabled_accessibility_services com.ezremote.tv/.service.EzTVControlService
adb shell settings put secure accessibility_enabled 1
```

---

## 🔒 Security & Privacy

- **Local Network Isolated**: EzRemote TV operates strictly within your local Wi-Fi / LAN network. No data or telemetry is transmitted to external servers.
- **PIN Session Protection**: Unauthenticated devices on the local network cannot send commands without entering the TV's 4-digit security PIN.

---

## 📜 Technical Stack

- **Host (Android TV)**: Java / Android SDK (API 24+), Embedded NanoWSD (HTTP + WebSockets), ZXing QR Generator, AccessibilityService.
- **Web Frontend**: HTML5, Modern Vanilla CSS (Glassmorphic dark theme, CSS Variables), JavaScript (WebSocket API, Web Vibration API, Touch Events).

---

## 📄 License

This project is distributed under the MIT License. See [LICENSE](LICENSE) for details.

Developed with ❤️ by [Alex Soh](https://github.com/alexsoh)
