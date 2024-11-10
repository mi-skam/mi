---
created: 2024-08-26T22:47:35+02:00
modified: 2024-10-17T22:25:32+02:00
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
- PowerShell als Default Shell für OpenSSH einrichten[^2]
- öffentlichen Schlüssel nach `__PROGRAMDATA__/ssh/administrators_authorized_keys` kopieren[^1]

[^1]: [[Updating authorized keys on OpenSSH Windows#^3de869]]
[^2]: [[Configuring the default shell for OpenSSH in Windows#^e853cb]]