# Smart Port Scanner - Documentation

## Overview
A comprehensive, Python-based Nmap wrapper designed for reliability, stealth, and detailed analysis. It features "Smart Retry" logic to unmask firewalled ports and a "Matrix" themed UI.

## Features
-   **Three Scanning Modes**:
    -   `fast`: Top 100 TCP (and Top 100 UDP if root).
    -   `default`: All TCP + Top 20 UDP.
    -   `slow`: All TCP + All UDP.
-   **Smart Retry**: Automatically re-scans `filtered` ports using advanced flags (`-sA`, `-sW`, `-sF`, `-sX`, `-sM`, `-sN`) to identify their true state.
-   **Matrix UI**: Minimalist, hacker-style Green/Black interface.
-   **Deep Analysis**: Consolidates results from multiple scans, prioritizing "Open" states.
-   **Root Intelligence**: Automatically degrades to unprivileged scans if not run as root.

## Usage

### 1. Requirements
-   Python 3
-   Nmap installed (`sudo apt install nmap`)
-   `rich` library (`pip install rich`)

### 2. Running a Scan
**Basic Usage (Default Mode):**
```bash
sudo ./scanner.py <target_ip>
```

**Fast Mode (Quick check):**
```bash
sudo ./scanner.py <target_ip> --mode fast
```

**Slow Mode (Full exhaustive):**
```bash
sudo ./scanner.py <target_ip> --mode slow
```

**Disable UDP (Faster):**
```bash
sudo ./scanner.py <target_ip> --no-udp
```

### 3. Understanding Results
-   **UNLOCKED** (Green): Port is open and accessible.
-   **LOCKED** (Red): Port is closed (responded with RST).
-   **HIDDEN** (Yellow): Port is filtered (no response or ICMP prohibited).
