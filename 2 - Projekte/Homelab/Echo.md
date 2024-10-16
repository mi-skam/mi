---
created: 2024-08-26T22:47:35+02:00
modified: 2024-10-07T13:31:29+02:00
description: Windows 11 vm, running on mbp
status: active
roles:
  - vm
  - dev
os: Windows 11
ip: 10.254.100.10
tags:
  - homelab
---

- Installation von Windows 11 Pro ARM64
- User: plumps
- Updates installieren
- OpenSSH-Server installieren (System > Optionale Features)
- OpenSSH-Server automatisch starten
- Windows PowerShell als defaultShell setzen[^1]
- öffentlichen Schlüssel nach `__PROGRAMDATA__/ssh/administrators_authorized_keys` kopieren[^2]

[^1]: `New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force`
[^2]: `$filePath = $env:ProgramData + "\ssh\administrators_authorized_keys"`
	`Set-Content -Path $filePath -Value "<content of ssh pub key>"`