---
dg-publish: true
created: 2024-08-02T10:27:06+02:00
modified: 2024-08-26T22:11:56+02:00
---

## Tracking
Signatur: "Kunde - Projekt - Thema"
Genauigkeit: 15min

Excel-Export

alles Wissen im OneNote "[Maksim - ARCHIprocess](https://onedrive.live.com/redir?resid=C834148EFC0CFB2D%2152690&page=Edit&wd=target%28Allgemein.one%7C9d1e669d-c242-42ac-a0e5-1f86d5a0a39e%2FMaksim%20Bronsky%20-%20ARCHIprocess%7Cbab00bfd-d3c0-4225-a491-254fd5d2d8e0%2F%29&wdorigin=NavigationUrl)"

Namenschema: Vorname-(C,S,D)admin (c = client, s = server, d = domain controller)


> [!WARNING] SSH-Login
> Auch bei konfiguriertem ssh-key muss man sich noch mit dem Domänen-Kennwort einloggen.

## Powershell

```shell
# ssh auf jumphost
ssh -t archiprocess.selfhost.eu -- powershell.exe
```

```powershell
$username = "ARCHIprocess\Maksim-HVadm"
$password = Read-Host -AsSecureString
$cred = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $username,$password

Get-VM -ComputerName apsrvhv2 -Credential $cred
```


## Microsoft RDP macOS

`fn`+`control`+`option`+`delete`


## Nvidia RTX A5000 virtualisieren

Unmount from Host, mount to VM
```powershell
# disable the host device
$location = "PCIROOT(0)#PCI(0101)#PCI(0000)"
$vm = "APVWSGPU3"
# disable the GPU in the device manager, find a powershell command
Dismount-VMHostAssignableDevice -force -LocationPath $location
Add-VMAssignableDevice -LocationPath $location -VMName $vm
```

Unmount from VM, attach to Host

```powershell
Remove-VMAssignableDevice -LocationPath $location -VMName $vm
Mount-VMHostAssignableDevice -LocationPath $location
# enable the device in the device manager, find a powershell command
```


### DDA
Wir versuchen uns an DDA (direct device assignment)
https://armann-systems.com/wiki/microsoft-hyper-v-grafikkarten-unterstuetzung-mit-dda/
https://docs.nvidia.com/vgpu/latest/grid-vgpu-user-guide/index.html#using-gpu-pass-through-windows-server-hyper-v

https://www.tenforums.com/virtualization/195745-tutorial-passing-through-gpu-hyper-v-guest-vm.html

https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/deploying-graphics-devices-using-dda
https://forums.developer.nvidia.com/t/multiple-gpu-assignments-to-a-single-hyper-v-vm-with-dda/274238/2

> [!quote]- [Nicklas Thomsen](https://learn.microsoft.com/en-us/users/na/?userid=96ef78b5-0000-0006-0000-000000000000) https://learn.microsoft.com/en-us/answers/questions/1254192/hyper-v-easy-gpu-pv-how-dose-the-gpu-partitioning
> Hello Thomas,
> 
> It's an interesting question, and not something that James Stringer writes alot about in his readme.
> 
> _While i am a subject matter expert on Hyper-V, this is merely my speculation_
> 
> James mentions he is using GPU technologies from **WSL2** and **Windows Sandbox**.
> 
> Both technologies uses the **Hyper-V** technology to abstract the hardware layer and give you a Virtual Machine.
> 
> But i do not think James uses the _real_ GPU partitioning technology for Hyper-V which has only just been released for Windows Server 2025 (Hyper-V server) as this has strict hardware requirements for the GPU:
> 
> [https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/gpu-partitioning?pivots=windows-server](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/gpu-partitioning?pivots=windows-server)
> 
> However, i think James uses the WDDM GPU Virtualization technology, which is a part of **Windows Sandbox** (which again is based on the overall Hyper-V Virtualization technology)
> 
> [https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-architecture#wddm-gpu-virtualization](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-architecture#wddm-gpu-virtualization)
> 
> That would explain why you are able to use **consumer** GPU's for your virtual machines, and aren't limited to the strict GPU requirements.
> 
> This works fine for a Windows Sandbox environment, where **security** isn't of a concern, since you are only allowed to run **1** Windows Sandbox instance by default.  
> From the Notes on Windows Sandbox Documentation
> 
> `Note`
> 
> `Enabling virtualized GPU can potentially increase the attack surface of the sandbox.`  
> This is OK when running 1 VM on your own machine sharing the same GPU Kernel, but unacceptable when hosting multiple VM's for a number of customers.
> 
> It would seem to me that James has figured out a way to use the WDDM GPU Virtualization solution against a normal Hyper-V VM, and not only the Windows Sandbox VM.
> 
> That would explain why the underlying VM that you create are so dependent on the host GPU drivers, because it uses the WDDM GPU Virtualization method (shares GPU Kernel with the host) and not _true GPU partitioning_ like seen on Windows Server 2025, where the VM has a _true_ GPU partitioning and does not share GPU kernel with the host.
> 
> So yes, unlike Windows Sandbox, because of James implementation, it's likely presumed that GPU resources are still allocated even after the VM is powered off (is would be the case of a real GPU partitioning solution).  
> In Windows Sandbox, GPU resources are released once you exit the VM (it's destroyed) however, since this is a normal VM i presume it does not release WDDM Graphics resources.
> 
> [Razzmatazzz](https://github.com/Razzmatazzz) Interactive script also confirms my theory, since there is a feature to disable GPU acceleration of your VM's.
> 
> Hope this answers your question
> 
> Regards
> 
> Nicklas

https://learn.microsoft.com/de-de/windows-server/virtualization/hyper-v/gpu-partitioning?pivots=azure-stack-hci


PCIROOT(0)#PCI(0101)#PCI(0000) GPU
PCIROOT(0)#PCI(0101)#PCI(0001)
Dismount-VMHostAssignableDevice -LocationPath "PCIROOT(0)#PCI(0101)#PCI(0001)" -force
Dismount-VMHostAssignableDevice -LocationPath "PCIROOT(0)#PCI(0101)#PCI(0000)" -force

```powershell
Dismount-VMHostAssignableDevice -LocationPath gpu-device-location -force
```
```powershell
Add-VMAssignableDevice -LocationPath gpu-device-location -VMName vm-name
```



> [!WARNING] DDA Inkompatibilität seit Window Server 2019
> 



![[Screenshot 2024-08-05 224058.png]]




## HCI

[[Restrukturierung IT Infrastruktur PME]]
### Project Proxmox
https://av.tib.eu/media/45645

Hyperkonvergenz besteht in Proxmox aus ***OVS/Linux*** Bridge, ***Ceph*** und ***KVM/LXC*** 