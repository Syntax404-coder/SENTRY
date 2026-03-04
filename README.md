# Sentry: Advanced Process Monitoring & System Activity Tracker

**Sentry** is a high-performance Command-Line Interface (CLI) utility designed for power users, system administrators, and developers. Built entirely within the PowerShell environment, it bridges the gap between standard monitoring tools and kernel-level system manipulation.

As someone with a background in **Docker and Kubernetes**, you'll recognize the value of this tool's granular control—it brings the precision of container orchestration to the Windows native process environment.

---

## Project Overview

Modern operating systems often prioritize safety and user-friendliness over granular control. When a system is under heavy load or an application becomes unresponsive, graphical interfaces can be slow to launch. Sentry leverages the speed of the command console and the power of the .NET framework to provide an instant, lightweight dashboard for system management.

Unlike standard tools, Sentry allows for **"God Mode"** capabilities, utilizing C# method injection to access Windows API calls not natively exposed in PowerShell.

### Technical Performance Highlights

* **Low Overhead:** Operates with minimal RAM footprint compared to GUI alternatives.
* **Kernel-Level Access:** Interacts directly with `ntdll.dll` for process suspension.
* **Automation Ready:** Designed to be integrated into larger administrative scripts.

---

## Key Features

### 1. Deep Process Control

Beyond simple termination, Sentry offers advanced management for running tasks:

* **Tree Kill:** Forcefully terminates a parent process and all child sub-processes.
* **Freeze / Resume:** Uses `ntdll.dll` to suspend process threads in memory, allowing users to pause resource-heavy applications without closing them.
* **CPU Affinity:** Latch specific processes to physical CPU cores.
* **Priority Management:** Dynamically adjust process priority classes (Idle, Normal, High, RealTime).

### 2. Startup & Security Heuristics

* **BIOS Boot Analysis:** Retrieves the exact "Last BIOS Boot Time" (in seconds) from the Windows Event Log.
* **Shady Process Scanner:** Uses behavioral heuristics to flag potentially malicious processes based on unsigned code or suspicious file paths (AppData/Temp).
* **Network Sentinel:** Filters active TCP/UDP connections to identify applications establishing external communication.

---

## Documentation & Setup

### System Requirements

* **OS:** Windows 10/11 (64-bit).
* **Environment:** PowerShell 5.1 or PowerShell Core 7+.
* **Permissions:** Administrative privileges are **mandatory**.

### Installation & Execution

Sentry is a portable, single-file application. To get started:

1. **Unblock the script:**
```powershell
Unblock-File -Path .\Sentry.ps1

```


2. **Set Execution Policy:**
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

```


3. **Launch:**
```powershell
.\Sentry.ps1

```



---

## Technical Architecture

Sentry utilizes a hybrid architecture combining PowerShell scripting with .NET Framework integration, a workflow that mirrors the efficiency you've mastered in **Ruby and Generative AI** development.

| Component | Technology | Purpose |
| --- | --- | --- |
| **Engine** | PowerShell / .NET | Core logic and system interaction. |
| **API Bridge** | P/Invoke (C#) | Accessing `ntdll.dll` for thread manipulation. |
| **Storage** | JSON | Local activity logging and persistence. |
| **UI** | ANSI / ASCII | High-contrast, low-latency dashboard rendering. |

---

## Disclaimer

**Use with caution.** Sentry provides administrative access to critical system functions. Forcing the termination of system-critical processes (e.g., `csrss.exe`) will result in a Blue Screen of Death (BSOD). The authors are not responsible for data loss or system instability resulting from misuse.

---

## License

This project is open-source. Please see the `LICENSE` file for full distribution rights.

**Would you like me to help you generate a `LICENSE` file or a `.gitignore` to keep your repository clean?**
