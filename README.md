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
```
### Notes 

- **Graceful Close**: The PostMessage method is safer and avoids potential data loss.
- **Forceful Kill**: The taskkill method is more aggressive and may result in unsaved data being lost.
- **Admin Privileges**: If using taskkill, ensure the script runs with administrative privileges if necessary.

### Contributing
Contributions are welcome! If you have any suggestions, improvements, or bug fixes, feel free to open an issue or submit a pull request. Here’s how you can contribute:

Fork the Repository: Create a fork of this repository.

Make Your Changes: Implement your changes or fixes.

Submit a Pull Request: Open a pull request with a detailed description of your changes.

### Support
If you find this script useful, consider giving it a ⭐️ on GitHub! For questions or issues, please open an issue in the repository.

Enjoy using the script! 🚀
