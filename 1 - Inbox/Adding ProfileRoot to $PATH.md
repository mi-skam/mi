---
up: 
related: 
created: 2024-05-31
modified: 2024-09-03T18:29:05+02:00
---
Add this to `$PROFILE`

```powershell
$ProfileRoot = (Split-Path -Parent $MyInvocation.MyCommand.Path)
$env:path += ";$ProfileRoot"
```