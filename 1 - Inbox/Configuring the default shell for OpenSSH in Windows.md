---
modified: 2024-10-17T22:17:11+02:00
---
Found in[^1] ^06b135

Example:

**Change openssh default shell to pwsh**

```powershell
$pwsh = "C:\Program Files\WindowsApps\Microsoft.PowerShell_7.4.5.0_arm64__8wekyb3d8bbwe\pwsh.exe"

New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value $pwsh -PropertyType String -Force
```

^e853cb

[^1]: https://learn.microsoft.com/en-us/windows-server/administration/OpenSSH/openssh-server-configuration#configuring-the-default-shell-for-openssh-in-windows