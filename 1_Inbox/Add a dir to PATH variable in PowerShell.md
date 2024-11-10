---
modified: 2024-10-16T17:21:22+02:00
---
We have two options[^1]:
1. Add it in `$PROFILE`
2. Use `[System.Environment]::SetEnvironmentVariable('Path', <new_path_value>, Machine|User)`

Example:

**Add `C:\Tools` to $PATH in the machine scope**

```powershell
$currentPath = [System.Environment]::GetEnvironmentVariable('Path')

# add a path "C:\Tools" to $PATH
[System.Environment]::SetEnvironmentVariable("Path", $currentPath + ";C:\Tools" , "Machine")

# delete a variable permanently
[System.Environment]::SetEnvironmentVariable("Foo", "" , "Machine")
```



[^1]: taken from `about_Environment_Variables`