---
modified: 2024-09-11T17:37:03+02:00
---
## Vorbereitungen

```powershell
Get-NetAdapter # listet alle Netzwerkkarten auf
$nic = (Get-NetAdapter).Name[0] # speichert den Namen des ersten Netzwerkadapters
$ip = 192.168.100.2
$ipDefaultGw = 192.168.100.1
$computerName = "dc01"
$domain = "mydomain.local"
$netbios = "MYDOMAIN"
$safeModeAdminPassword = "superS3CR3T"
```

Netztwerkeinstellungen:
- DHCP deaktivieren
- IP-Adresse festlegen
- DNS ändern
- IPv6 deaktivieren
- Server umbenennen

```powershell
Set-NetIPInterface -InterfaceAlias $nic -AddressFamily IPv4 -DHCP Disabled -PassThru
New-NetIP -InterfaceAlias $nic -AddressFamily IPv4 -IPAddress $ip -PrefixLength 24 -DefaultGateway $ipDefaultGw
Set-DnsClientServerAddress -InterfaceAlias $nic -ServerAddresses $ip
Disable-NetAdapterBinding -Name $nic -ComponentID ms_tcpip6
Rename-Computer -NewName $computerName -Restart -Force
```

## Installation der (ersten) DCs

```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools -IncludeAllSubFeature
```

```powershell
# interaktiv
$pwd = Read-Host "Enter the SafeModeAdminPassword" -AsSecureString # interaktiv

# nicht-interaktive Alternative zum Scripten
$pwd = ConvertTo-SecureString $safeModeAdminPassword -AsPlaintext -Force

# erster DC
Install-ADDSForest `
-DomainName $domain -DomainNetBiosName $netbios `
-DomainMode WinThreshold -ForestMode WinThreshold `
-SkipPreChecks `
-InstallDns:$true `
-SafeModeAdministratorPassword $pwd `
-Force

# zweiter, dritter, vierter, ... DC

Install-ADDSDomainController -Credential $cred `
-DomainName $domain `
-SkipPreChecks `
-NoGlobalCatalog:$false `
-CriticalReplicationOnly:$false `
-InstallDns:$true `
-SiteName "Default-First-Site-Name" `
-SafeModeAdministratorPassword $pwd `
-Force
```

## Grundlegende DNS-Konfiguration

Mit `nslookup` kann ich Informationen über die DNS-Auflösung einholen (DNS-Server etc), Hostnames auflösen.

DNS-Zonen abfragen `Get-DnsServerZone`
Reverse-Lookup-Zone hinzufügen: 
```powershell
Add-DnsServerPrimaryZone -NetworkID 192.168.100.0/24 -ReplicationScope Domain -DynamicUpdate Secure -PassThru
```
DNS-Server registrieren `ipconfig /registerdns`
DNS nochmal ändern, da dieser auf `127.0.0.1` gesetzt wurde: `Set-DnsClientServerAddress -InterfaceAlias $nic -ServerAddresses $ip`

DNS-Forwarder konfigurieren: `Set-DnsServerForwarder -IPAddress $ipDefaultGW, 8.8.8.8`