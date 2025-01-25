# AutoHotkey Script: Force Close Active Window

This AutoHotkey (AHK) script allows you to forcefully close the currently active window by pressing a customizable hotkey (`Ctrl + Del` by default). It provides both a graceful close method (sending a close signal to the window) and an aggressive method (forcefully terminating the process).

---

## Features

- **Hotkey Support**: Press `Ctrl + Del` to close the active window.
- **Graceful Close**: Sends a `WM_SYSCOMMAND` message to the window, simulating a click on the "X" button.
- **Forceful Termination**: Optionally uses `taskkill` to forcefully terminate the process associated with the active window.
- **Customizable**: Easily modify the hotkey or behavior to suit your needs.

---

## How It Works

1. The script detects the active window using `WinGet`.
2. When the hotkey is pressed, it sends a close signal (`WM_SYSCOMMAND` with `SC_CLOSE`) to the active window.
3. If the window does not close gracefully, you can uncomment the `taskkill` section to forcefully terminate the process.

---

## Usage

### Prerequisites

- **AutoHotkey**: Download and install AutoHotkey from [https://www.autohotkey.com/](https://www.autohotkey.com/).

### Steps

1. **Download the Script**:
   - Clone this repository or download the `ForceClose.ahk` file.
2. **Run the Script**:
   - Double-click the `ForceClose.ahk` file to execute the script.
3. **Use the Hotkey**:
   - Press `Ctrl + Del` while any window is active to close it.

---

## Script Code

```ahk
^Delete::  ; Ctrl + Del hotkey
    ; Get the ID of the active window
    WinGet, ActiveWindowID, ID, A
    ; Forcefully close the active window
    PostMessage, 0x112, 0xF060,,, ahk_id %ActiveWindowID%  ; Send WM_SYSCOMMAND, SC_CLOSE
    ; Alternatively, use the more aggressive method to kill the process
    ; WinGet, ProcessName, ProcessName, ahk_id %ActiveWindowID%
    ; Run, taskkill /f /im %ProcessName%,, Hide
return
