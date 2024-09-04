---
created: 2024-08-26T22:47:35+02:00
modified: 2024-08-28T07:13:04+02:00
---

- Installation von Windows 11 Pro ARM64
- User: Maksim, Passwort: Maksim
- Updates installieren
- OpenSSH-Server installieren (System > Optionale Features)
- OpenSSH-Server automatisch starten
- Windows PowerShell als defaultShell setzen[^1]
- öffentlichen Schlüssel nach `__PROGRAMDATA__/ssh/administrators_authorized_keys` kopieren

[^1]: `New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force`