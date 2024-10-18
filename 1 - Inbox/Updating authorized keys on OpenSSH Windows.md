---
modified: 2024-10-17T22:37:54+02:00
---
## User

öffentlichen Schlüssel nach `__HOME__/.ssh/authorized_keys` kopieren

```powershell
$filePath = $env:HOME + "\.ssh\authorized_keys"

Set-Content -Path $filePath -Value "<content of ssh pub key>"
```

## Administrator

öffentlichen Schlüssel nach `__PROGRAMDATA__/ssh/administrators_authorized_keys` kopieren

```powershell
$filePath = $env:ProgramData + "\ssh\administrators_authorized_keys"

Set-Content -Path $filePath -Value "<content of ssh pub key>"
```

^3de869
