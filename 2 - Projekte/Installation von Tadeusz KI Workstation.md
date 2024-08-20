---
created: 2024-06-20
tags:
---

## Bios

interne GPU muss als primary deklariert werden

## Proxmox

We load some additional modules, needed for accessing the `IOMMU` capabilities. Before doing that, we need to make sure we enable `IOMMU`  in the Bios / Firmware settings.

> */etc/modules.d/passthrough*
> ```shell
> vfio
> vfio_iommu_type1
> vfio_pci
> vfio_virqfd
> ```

Additionally we need to set some kernel commandline options in `/etc/default/grub`. Add `nomodeset` and `amd_iommu=on`

> * Look at the iommu groups*
> `dmesg | grep iommu`

## Windows VM
> *virtio-win.iso*
> - guest-agent installieren
> - storage driver (installation)

### PCIe Passthrough der Nvidia 

In the next step we blacklist the drivers for the GPU (`nouveau` and `nvidia`) to prevent their initialisation.  
```shell
# find gpu
$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation Device 2705 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 22bb (rev a1)
# find gpu pci id's
$ lspci -n -s 01:00
01:00.0 0300: 10de:2705 (rev a1) # we need 10de:2705 and
01:00.1 0403: 10de:22bb (rev a1) # 10de:22bb for our passthrough.conf
```

> */etc/modprobe.d/passthrough.conf*
> ```shell
> blacklist nouveau
> blacklist nvidia
> 
> options kvm ignore_msrs=1
> options vfio_iommu_type1 allow_unsafe_interrupts=1
> options vfio-pci ids=10de:2705,10de:22bb disable_vga=1
> ```

Apply all changes

`update-initramfs -u -k all`

Check if the gpu is now in control of `vfio-pci` instead of a graphics driver, look for `Kernel driver in use`  by using `lspci -n -s 01:00`.

### Adding the GPU to the VM
![[Pasted image 20240621090139.png]]