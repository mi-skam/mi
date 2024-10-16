---
created: 2024-08-26T22:47:35+02:00
modified: 2024-09-21T15:07:27+02:00
status: inactive
---

- Installation von Windows 11 Pro ARM64
- User: Maksim, Passwort: Maksim
- Updates installieren
- OpenSSH-Server installieren (System > Optionale Features)
- OpenSSH-Server automatisch starten
- Windows PowerShell als defaultShell setzen[^1]
- öffentlichen Schlüssel nach `__PROGRAMDATA__/ssh/administrators_authorized_keys` kopieren

[^1]: `New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force`