---
summary: 
attendees: 
tags:
  - meeting
created: 2024-10-14 10:12
cssclasses:
  - wide
modified: 2024-10-17T11:18:58+02:00
---
![[20241014-16_PowerShell_Kurs_Carsten_Eric.pdf]]
##  📝 Notes

## Tag 1 

![[Pasted image 20241014101237.png]]


### Einführung

Meine Fragen
- Wie verhalten sich die beiden Dialekte zueinander?
- Wieso gibt es so viele Cmdlets nicht in der pwsh?
- about Files sind Plural?
- -Fragen zu den Parametern-

- -ISE gegen VSCODE langfristig tauschen-
- es gibt also powershell.exe, pwsh und azure powershell

```powershell
Get-ExecutionPolicy # wer darf Skripte ausführen?
Set-ExecutionPolicy Unrestricted
```

### Cmdlets

![[Pasted image 20241014110806.png]]
![[Pasted image 20241014110816.png]]


> [!caution] Immer Singular!
> Commandlets wollen Substantive im Singular, auch wenn es sich um Plural handelt

![[Pasted image 20241014111327.png]]
### Hilfe

```pwsh
get-help about* #alle Hilfethemen
```

### Module

![[Pasted image 20241014112145.png]]

```powershell
Get-Module # zeigt die geladenen Module
Get-Module -ListAvailable # ... alle Module
Import-Module # lädt ein Modul
Get-Command -Module PackageManagement # zeigt alle Cmdlets eines Moduls
```

![[Pasted image 20241014112537.png]]

![[Pasted image 20241014113000.png]]

![[Pasted image 20241014113155.png]]

- positional parameter für den Schalter: `[ ]`
- optional parameter: Schalter und Typ in eckigen Klammern
- mandatory paramater: nicht in eckigen Klammern

![[Pasted image 20241014130532.png]]

![[Pasted image 20241014145534.png]]

```powershell

# hyper-v vm erstellen
New-VM -Name ... -MemoryStartupBytes ...GB -Generation 2 -Path C:\VM\
New-VHD -Path ... -SizeBytes -Dynamic
Add-VMHardDiskDrive -VMName DC01 -Path ...
Add-VMDvdDrive -VMName DC01 -Path ...

# installation lässt nicht mit bord-eigenen Mitteln automatisieren
Administrator / admin.1234

Spannend, man kann die VMs direkt über VMBUS HyperV direct erreichen -VMName

# domain einrichten

# 5 test-user im ad einrichten
# dns eintrag

New-VMSwitch -Name ComputeSwitch -NetAdapterName VMSwitchNic1, VMSwitchNIC2
Get-VMNetworkAdapter -VMName DC01 | Connect-VMNetworkAdapter -SwitchName ComputeSwitch

```



get-windowsfeature
Install-WindowsFeature AD-Domain-Services -IncludeAllSubFeature -IncludeManagementTools


#### Powershell Pipeline

![[Pasted image 20241014163035.png]]
![[Pasted image 20241014163246.png]]

Manchmal braucht es nicht nur die richtigen Values sondern auch die richtigen key/value pairs

![[Pasted image 20241014164803.png]]

![[Pasted image 20241014165335.png]]

## Tag 2

![[Pasted image 20241014170300.png]]

![[Pasted image 20241015091913.png]]
Erzeugt eine Set-Switch `New-VMSwitch -Name ComputeSwitch -NetAdapterName VMSwitchNic1, VMSwitchNIC2 -EnableEmbeddedTeaming $true` 

- [ ] Was ist eine Set-Switch? #pme


![[Pasted image 20241015093028.png]]

1. `gps TextEdit | ConvertTo-Csv | Out-File process.csv` `import-csv ./process.csv | stop-process`
2. `(Measure-Command { gps TextEdit }).TotalSeconds` `(Measure-Command { gps | where-object Name -eq TextEdit }).TotalSeconds`
3. `gsv | where {$_.Name.Length -le 5 }`


![[Pasted image 20241015100908.png]]
![[Pasted image 20241015101213.png]]

get-volume zeigt die Festplatten an

![[Pasted image 20241015101605.png]]

#### Variablen
- nur alnum
- nicht case-sensitiv
- typecasting wie in JS

```powershell
$zahl = 5
# setzt den Wert von $hallo auf "Welt" 
$string = "hallo"
Set-Variable $string -Value "Welt"
#expliziter Type, type-cast
[string]$hello = 3

# variable löschen
$variable = $null
remove-variable $variable

# type
$zahl.GetType()
```

Typen
- String
- Int32
- DateTime

Arrays

```powershell
$array = @()
[Array]$user = "value"
```

Hash Tables
- nicht so verbreitet wie Liste, Objekte

```powershell
$hash = @{}
$hash.['test'] = ...
```

Skripte
Wann?
- Wiederholende Aufgaben
- Komplexe Aufgaben
- Reporting

Skript-Sicherheit
- mit Pfad aufrufen (absolut, relativ)

![[Pasted image 20241015112757.png]]

Conditionals und Loops

![[Pasted image 20241015113832.png]]

User Interaktion
![[Pasted image 20241015114611.png]]

![[Pasted image 20241015115616.png]]

![[Pasted image 20241015141452.png]]
![[Pasted image 20241015143153.png]]
comment-help baut einen Boilerplate für die Hilfe

![[Pasted image 20241015150750.png]]
![[Pasted image 20241015151038.png]]
## Tag 3 

![[Pasted image 20241014101358.png]]

### Azure DevOps

![[Pasted image 20241016102358.png]]
![[Pasted image 20241016102503.png]]

![[Pasted image 20241016102906.png]]

![[Pasted image 20241016103403.png]]
![[Pasted image 20241016103954.png]]
![[Pasted image 20241016153631.png]]