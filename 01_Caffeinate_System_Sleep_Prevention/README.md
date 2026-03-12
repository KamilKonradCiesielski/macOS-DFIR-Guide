# ☕ Caffeinate - Prevention of System Sleep

A native macOS utility used to prevent the processor, disk, or display from sleeping. This is a critical tool during live triage and imaging to maintain system access and prevent data encryption lockouts.

## ⚡ Quick Start (Recommended)

The safest combination for evidence preservation:

```bash
caffeinate -dis
```

Effect: Keeps the display on, ignores user idle timers, and prevents the system from entering sleep mode.

# 🔍 Flags and Definitions
Flag
Name
DFIR Context: 
```bash
-d
```
Display
Prevents the display from dimming/sleeping. Crucial to avoid the Lock Screen.
```bash
-i
```
Idle
Prevents sleep caused by system idleness (no mouse/keyboard input).
```bash
-s
```
System
Prevents the entire system from sleeping while on AC power.

# 🛠️ Advanced Scenarios
1. Timed Prevention
If you know the triage/imaging will take a specific amount of time (e.g., 2 hours = 7200 seconds):
```bash
caffeinate -dis -t 7200
```

2. Bind to a Specific Process
caffeinate will run automatically until the specified Process ID (e.g., FTK Imager PID) finishes:
```bash
caffeinate -dis -w <PID>
```

🛑 Termination
* To stop the process and allow the system to sleep normally, use Ctrl + C in the terminal window.

# ⚠️ Warning!
* A Running caffeinate leaves traces in system logs (e.g., powertop, pmset). Always document the exact time and command used in your forensic report. By default, caffeinate may fail if the laptop lid is closed, unless the Mac is connected to both power and an external display.Never close the laptop lid during live forensics or imaging.
