---
created: 2023-12-12
modified: 2024-09-03T17:08:14+02:00
---
To save a lot of memory in WSL, you can disable[^1] **WSL-G**, the graphical user interface subsystem. 🙃👍

## Installation

### with DISM

```shell
# Enable WSL2
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Enable VM Platform for WSL2
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

## Configuration

.wslconfig

```ini
[wsl2]
guiApplications=false
```

[^1]: https://github.com/microsoft/wslg#wslg-system-distro
