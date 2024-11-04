---
modified: 2024-11-03T08:22:45+01:00
tags:
  - pme
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
