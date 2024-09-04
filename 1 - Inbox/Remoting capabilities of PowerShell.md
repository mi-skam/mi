---
created: 2024-08-07
tags: 
modified: 2024-08-30 10:48
---
PowerShell has a twofold support for accessing remote session. The windows only protocol **WInRM** and the newer **OpenSSH**. 
[[2024-08-30]] As my knowledge goes the support is not 100% for `OpenSSH`

> [!WARNING]+ Domain name for user needs to be upper case!
> username@domain is wrong ❌
> username@DOMAIN is right ✅
> 


### Installation of WS support
```bash
sudo pwsh -Command 'Install-Module -Name PSWSMan'
sudo pwsh -Command 'Install-WSMan'
```
### Validation

```powershell
$cred=Get-Credential 
Enter-PSSession -ComputerName vmhostname.vmdomain -Credential $cred -Authentication Negotiate
```
### File Copy
```powershell
$pw = convertto-securestring -AsPlainText -Force -String PASS
$cred = new-object -typename System.Management.Automation.PSCredential -argumentlist "USER",$pw
$session = New-PSSession -ComputerName win10pro.localdomain -Credential $cred  -Authentication Negotiate
Copy-Item -Path 'C:\Users\USER\Desktop\somefile.txt' -Destination /tmp/ -FromSession $session
```