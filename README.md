# ⚡ ADB Optimization and Debloat Guide for Tecno Spark 10C (Unisoc T606)
**A Systemic Flow Project**

<div align="center">

🌐 **Languages / Idiomas:**

[🇺🇸 English](README.md) | [🇪🇸 Español](README_ES.md)

</div>

![Android](https://img.shields.io/badge/Android-12%2B-34A853?style=for-the-badge&logo=android&logoColor=white)
![ADB](https://img.shields.io/badge/ADB-Debloat%20%26%20Tuning-000000?style=for-the-badge&logo=android&logoColor=white)
![Chipset](https://img.shields.io/badge/Unisoc-T606-FF6600?style=for-the-badge)
![HiOS](https://img.shields.io/badge/HiOS-Optimized-6C5CE7?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

This guide provides a complete, **100% safe, no-root** method to optimize the performance of the **Tecno Spark 10C (Unisoc T606)** running HiOS. It allows you to recover up to **2.1 GB of free RAM at idle**, reduce touch latency, and remove background telemetry and factory bloatware.

---

## 📌 Key Features
* **Performance Boost:** Massive RAM recovery (~2.1 GB free at idle / ~1.5 GB under heavy load).
* **SoC Tailored:** Specifically tuned for the Unisoc T606 architecture.
* **Safe & Stable:** Keeps Tecno ID, cloud sync, and the Ella virtual assistant fully functional.

---

## 📁 1. Master Bloatware Removal List

The following packages are safely uninstalled via ADB:

### 🚫 Ads, Stores & Telemetry (Transsion / HiOS)
* `com.transsnet.store` (PalmStore - Secondary Store)
* `net.bat.store` (AHA Games - Game Catalog)
* `com.talpa.hibrowser` (Stock Browser)
* `com.talpa.hiservice` (Secondary Brand Services)
* `com.transsion.statisticalsales` (Sales Tracker / Telemetry)
* `com.transsion.chromecustomization` (Carrier Customizations)

### 📦 System Bloat & Diagnostics
* `com.transsion.tecnospot` (Tecno Spot Community Forum)
* `com.transsion.carlcare` (Carlcare Tech Support)
* `com.transsion.fmradio` (Analog FM Radio)
* `com.transsion.childmode` (Kids Mode)
* `com.transsion.hiparty` (Hi Party Music App)
* `com.transsion.letswitch` (Data Migration Tool)
* `com.idea.questionnaire` (System Feedback Surveys)
* `com.transsion.trancare` (Background Diagnostic Service)
* `com.transsion.repaircard` (Virtual Warranty Card)
* `com.transsion.beez` (Unnecessary HiOS Component)
* `com.transsion.tabe` (Unnecessary HiOS Component)
* `com.transsion.teop` (Unnecessary HiOS Component)

### 👥 Hidden Facebook Services (Trackers)
* `com.facebook.services` (Facebook Background Services)
* `com.facebook.system` (Facebook Hidden Installer)
* `com.facebook.appmanager` (Facebook App Manager)

### 🤖 Secondary Google Tools
* `com.google.android.apps.youtube.music` (YouTube Music)
* `com.google.android.projection.gearhead` (Android Auto)
* `com.google.android.apps.wellbeing` (Digital Wellbeing)
* `com.google.android.feedback` (Constant Error Reporting)

---

## 🛠️ 2. Execution ADB Commands

Run these blocks sequentially in your terminal with USB Debugging enabled on your phone:

### Step A: Bloatware Removal
```bash
adb shell pm uninstall -k --user 0 com.transsnet.store
adb shell pm uninstall -k --user 0 net.bat.store
adb shell pm uninstall -k --user 0 com.talpa.hibrowser
adb shell pm uninstall -k --user 0 com.talpa.hiservice
adb shell pm uninstall -k --user 0 com.transsion.statisticalsales
adb shell pm uninstall -k --user 0 com.transsion.chromecustomization
adb shell pm uninstall -k --user 0 com.transsion.tecnospot
adb shell pm uninstall -k --user 0 com.transsion.carlcare
adb shell pm uninstall -k --user 0 com.transsion.fmradio
adb shell pm uninstall -k --user 0 com.transsion.childmode
adb shell pm uninstall -k --user 0 com.transsion.hiparty
adb shell pm uninstall -k --user 0 com.transsion.letswitch
adb shell pm uninstall -k --user 0 com.idea.questionnaire
adb shell pm uninstall -k --user 0 com.transsion.trancare
adb shell pm uninstall -k --user 0 com.transsion.repaircard
adb shell pm uninstall -k --user 0 com.transsion.beez
adb shell pm uninstall -k --user 0 com.transsion.tabe
adb shell pm uninstall -k --user 0 com.transsion.teop
adb shell pm uninstall -k --user 0 com.facebook.services
adb shell pm uninstall -k --user 0 com.facebook.system
adb shell pm uninstall -k --user 0 com.facebook.appmanager
adb shell pm uninstall -k --user 0 com.google.android.apps.youtube.music
adb shell pm uninstall -k --user 0 com.google.android.projection.gearhead
adb shell pm uninstall -k --user 0 com.google.android.apps.wellbeing
adb shell pm uninstall -k --user 0 com.google.android.feedback
```

### Step B: Performance & Touch Tuning
```bash
adb shell settings put global hardware_accelerated_rendering true
adb shell settings put system touch_pump_rate 1
adb shell settings put secure long_press_timeout 200
adb shell settings put global app_standby_enabled 0
```

### Step C: ART Optimization (Advanced Compilation Options)

* **Full system recompilation (Ideal for initial setup):**
```bash
  adb shell cmd package compile -m speed -a
```

* **Compile a single specific package (For new or individual apps without full recompilation):**
```bash
  adb shell cmd package compile -m speed <package_name>
```

* **Reset/Decompile a specific application profile:**
```bash
  adb shell cmd package compile --reset <package_name>
```

* **Reset/Decompile all packages in the system:**
```bash
  adb shell cmd package compile --reset -a
```

---

## 🔒 3. Whitelist (Protected Components)

To ensure HiOS system stability and prevent bootloops, **DO NOT** uninstall the following packages:

* `tech.palm.id` (Tecno ID / Account Sync)
* `com.transsion.notebook` (Stock Notes App)
* `com.transsion.hilauncher` (HiOS Interface Launcher)
* `com.transsion.kolun.assistant` (Ella Voice Assistant)
* `com.google.android.apps.photos` (Google Photos)

---

## 📜 License
Published under the **MIT** license by **Systemic Flow**.
