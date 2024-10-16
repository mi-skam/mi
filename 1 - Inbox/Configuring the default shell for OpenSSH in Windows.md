---
modified: 2024-10-16T17:24:33+02:00
---

Found in[^1]

Example:

**Change openssh default shell to pwsh**

```powershell
$pwsh = "C:\Program Files\WindowsApps\Microsoft.PowerShell_7.4.5.0_arm64__8wekyb3d8bbwe\pwsh.exe"

New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value $pwsh -PropertyType String -Force
```

[^1]: https://learn.microsoft.com/en-us/windows-server/administration/OpenSSH/openssh-server-configuration#configuring-the-default-shell-for-openssh-in-windows